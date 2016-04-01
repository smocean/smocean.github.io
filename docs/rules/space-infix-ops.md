---
title: Rule space-infix-ops
layout: doc
translator: molee1905
proofreader: maomaoking
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->

# Require Spaces Around Infix Operators (space-infix-ops)

# 要求中缀操作符周围有空格 (space-infix-ops)

While formatting preferences are very personal, a number of style guides require spaces around operators, such as:

虽然格式化首选项都非常个人化，但大量的风格指南要求运算符周围有空格，例如：

```js
var sum = 1 + 2;
```

The proponents of these extra spaces believe it make the code easier to read and can more easily highlight potential errors, such as:

这些额外空格的支持者认为它将使代码易于阅读，可以更轻易地突出潜在的错误，例如：

```js
var sum = i+++2;
```

While this is valid JavaScript syntax, it is hard to determine what the author intended.

虽然这是有效的Javascript语法，但很难确定作者的意图。

**Fixable:** This rule is automatically fixable using the `--fix` flag on the command line.

**Fixable:** 该规则可以通过`--fix`命令行进行自动修复。

## Rule Details

This rule is aimed at ensuring there are spaces around infix operators.

此规则旨在确保中缀运算符周围有空格。

## Options

This rule accepts a single options argument with the following defaults:

该规则接收唯一一个可选项参数，具有以下默认值：

```json
"space-infix-ops": [2, {"int32Hint": false}]
```

### `int32Hint`

Set the `int32Hint` option to `true` (default is `false`) to allow write `a|0` without space.

设置 `int32Hint` 选项为 `true` (默认 `false`) 允许 `a|0` 不带空格.

```js
var foo = bar|0; // `foo` is forced to be signed 32 bit integer
```

The following patterns are considered problems:

以下模式被认为是有问题的：

```js
/*eslint space-infix-ops: 2*/
/*eslint-env es6*/

a+b

a+ b

a +b

a?b:c

const a={b:1};

var {a=0}=bar;

function foo(a=0) { }
```

The following patterns are not considered problems:

以下模式被认为是没有问题的：

```js
/*eslint space-infix-ops: 2*/
/*eslint-env es6*/

a + b

a       + b

a ? b : c

const a = {b:1};

var {a = 0} = bar;

function foo(a = 0) { }
```

## Version

This rule was introduced in ESLint 0.2.0.

该规则在ESLint 0.2.0 中被引入。

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/space-infix-ops.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/space-infix-ops.md)
