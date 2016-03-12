---
title: Rule max-params
layout: doc
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->

# Limit Maximum Number of Parameters (max-params)

# 限制最大参数个数(max-params)

Functions that take numerous parameters can be difficult to read and write because it requires the memorization of what each parameter is, its type, and the order they should appear in. As a result, many coders adhere to a convention that caps the number of parameters a function can take.

函数如果有许多参数的话，会难以阅读和书写，因为要记住每个参数是什么，它的类型以及它们出现顺序。因此，许多程序员都约定一个函数中参数个数的上限。

```js
function foo (bar, baz, qux, qxx) { // four parameters, may be too many
    doSomething();
}
```

## Rule Details

This rule is aimed at making functions easier to read and write by capping the number of formal arguments a function can accept. As such it will warn when it encounters a function that accepts more than the configured maximum number of parameters.

该规则旨在通过限制函数中可接受的形参个数来使函数更有阅读和书写。因此，如果一个函数接收了超过配置的最大参数个数，该规则将发出警告。

The following patterns are considered problems:

以下模式被认为是有问题的：

```js
/*eslint max-params: [2, 3]*/

function foo (bar, baz, qux, qxx) {
    doSomething();
}
```

The following patterns are not considered problems:

以下模式被认为是没有问题的：

```js
/*eslint max-params: [2, 3]*/

function foo (bar, baz, qux) {
    doSomething();
}
```

Optionally, you may specify a `maximum` object property:

```json
"max-params": [2, 2]
```

is equivalent to

```json
"max-params": [2, {"maximum": 2}]
```


## Related Rules

* [complexity](complexity)
* [max-depth](max-depth)
* [max-len](max-len)
* [max-nested-callbacks](max-nested-callbacks)
* [max-statements](max-statements)

## Version

This rule was introduced in ESLint 0.0.9.

该规则在ESLint 0.0.9 中被引入。

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/max-params.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/max-params.md)
