---
title: Rule no-dupe-keys
layout: doc
translator: ybbjegj
proofreader: molee1905
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->
# Disallow Duplicate Keys (no-dupe-keys)

# 禁止重复的键 (no-dupe-keys)

Creating objects with duplicate keys in objects can cause unexpected behavior in your application. The `no-dupe-keys` rule flags the use of duplicate keys in object literals.

在你的应用程序中，创建有重复键的对象可能导致不可预测的行为。`no-dupe-keys`规则标记对象字面量中有使用重复键的情况。

```js
var foo = {
    bar: "baz",
    bar: "qux"
};
```

## Rule Details

This rule is aimed at preventing possible errors and unexpected behavior that might arise from using duplicate keys in object literals. As such, it warns whenever it finds a duplicate key.

该规则旨在防止在对象字面量中因使用重复的键而可能引起的错误和异常行为。 因此，只要有重复键，该规则就会发出警告。

The following patterns are considered problems:

以下模式被认为是有问题的：

```js
/*eslint no-dupe-keys: 2*/

var foo = {
    bar: "baz",
    bar: "qux"     /*error Duplicate key 'bar'.*/
};

var foo = {
    "bar": "baz",
    bar: "qux"     /*error Duplicate key 'bar'.*/
};

var foo = {
    0x1: "baz",
    1: "qux"       /*error Duplicate key '1'.*/
};
```

The following patterns are not considered problems:

以下模式被认为是没有问题的：

```js
/*eslint no-dupe-keys: 2*/

var foo = {
    bar: "baz",
    quxx: "qux"
};
```

## Version

This rule was introduced in ESLint 0.0.9.

该规则在 ESLint 0.0.9 中被引入。

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/no-dupe-keys.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/no-dupe-keys.md)
