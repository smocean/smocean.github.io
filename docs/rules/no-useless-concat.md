---
title: Rule no-useless-concat
layout: doc
translator: fengnana
proofreader: coocon 
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->
# Disallow unnecessary concatenation of strings (no-useless-concat)

# 禁止没有必要的字符拼接 (no-useless-concat)

It's unnecessary to concatenate two strings together, such as:

像这样把两个字符拼接在一起是没有必要的：

```js
var foo = "a" + "b";
```

This code is likely the result of refactoring where a variable was removed from the concatenation (such as `"a" + b + "b"`). In such a case, the concatenation isn't important and the code can be rewritten as:

上面的代码像是把一个变量从拼接中移除来重构结构，在这种情况下，拼接不是重要的，代码可以被写成如下形式:

```js
var foo = "ab";
```

## Rule Details

This rule aims to flag the concatenation of 2 literals when they could be combined into a single literal. Literals can be strings or template literals.

此规则目的在于标记2个字面量的拼接，当他们可以组合成一个单一的文本时。字面量可以是字符串或者模板字面量。

The following patterns are considered problems:

以下模式被认为是有问题的：

```js
/*eslint no-useless-concat: 2*/
/*eslint-env es6*/

// these are the same as "10"
var a = `some` + `string`;
var a = '1' + '0';
var a = '1' + `0`;
var a = `1` + '0';
var a = `1` + `0`;
```

The following patterns are not considered problems:

此规则被认为是没有问题的：

```js
/*eslint no-useless-concat: 2*/

// when a non string is included
var c = a + b;
var c = '1' + a;
var a = 1 + '1';
var c = 1 - 2;
// when the string concatenation is multiline
var c = "foo" +
    "bar";
```

## When Not To Use It

If you don't want to be notified about unnecessary string concatenation, you can safely disable this rule.

如果不想被通知存在没有必要的字符拼接，你可以安全的禁用此规则。

## Version

This rule was introduced in ESLint 1.3.0.

此规则在 ESLint 1.3.0 中被引入。

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/no-useless-concat.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/no-useless-concat.md)
