---
title: Rule no-unneeded-ternary
layout: doc
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->

# Disallow conditional expressions that can be expressed with simpler constructs (no-unneeded-ternary)

# 禁止可以表达为更简单的结构的条件表达式 (no-unneeded-ternary)

It's a common mistake in JavaScript to use a conditional expression to select between two Boolean values instead of using ! to convert the test to a Boolean.
Here are some examples:

在Javascript，一个常见的错误是使用一个条件表达式在两个Boolean值之间进行选择而不是使用！将测试条件转为一个Boolean类型。如以下示例：

```js
// Bad
var isYes = answer === 1 ? true : false;

// Good
var isYes = answer === 1;


// Bad
var isNo = answer === 1 ? false : true;

// Good
var isNo = answer !== 1;
```

This rule disallows the use of 'Boolean' literals inside conditional expressions.

该规则允许在条件表达式中使用'布尔型'文本。

Another common mistake is using a single variable as both the conditional test and the consequent. In such cases, the logical `OR` can be used to provide the same functionality.
Here is an example:

另一个常见的错误是使用单个变量同时作为测试条件和结果。在这种情况下，逻辑 `OR`操作符可以实现相同的功能。

如下所示：

```js
// Bad
var foo = bar ? bar : 1;

// Good
var foo = bar || 1;
```

This rule disallows the conditional expression as a default assignment pattern when the `defaultAssignment` option is set to `false`.

当`defaultAssignment`设置为`false`时，该规则不允许条件表达式直接赋值。

## Rule Details

This rule enforces a coding style where it disallows conditional expressions that can be implemented using simpler language constructs. Specifically, this rule disallows the use of Boolean literals inside conditional expressions, and conditional expressions where a single variable is used as both the test and consequent. This rule's default options are `{"defaultAssignment": true }`.

该规则强制一种代码风格，即不允许可以使用简单的语言结构实现的条件表达式。具体而言，该规则不允许在条件表达式中使用布尔型文本，也不允许条件表达式中单个变量既作测试条件也作结果。该规则默认选项为`{"defaultAssignment": true }`。

The following patterns are considered problems:

以下模式被认为是有问题的：

```js
/*eslint no-unneeded-ternary: 2*/

var a = x === 2 ? true : false;

var a = x ? true : false;
```

The following pattern is considered a warning when `defaultAssignment` is `false`:

当`defaultAssignment`设置为`false`时，以下模式被认为是有问题的：

```js
var a = x ? x : 1;
```

The following patterns are not considered problems:

以下模式被认为是没有问题的：

```js
/*eslint no-unneeded-ternary: 2*/

var a = x === 2 ? "Yes" : "No";

var a = x !== false;

var a = x ? "Yes" : "No";

var a = x ? y : x;
```

The following pattern is not considered a warning when `defaultAssignment` is `true`:

当`defaultAssignment`设置为`true`时，以下模式被认为是没有问题的：

```js
var a = x ? x : 1;
```

## When Not To Use It

You can turn this rule off if you are not concerned with unnecessary complexity in conditional expressions.

如果你不关心条件表达式中不必要的复杂性的话，可以关闭此规则。

## Related Rules

* [no-ternary](no-ternary)
* [no-nested-ternary](no-nested-ternary)

## Version

This rule was introduced in ESLint 0.21.0.

该规则在 ESLint 0.21.0 中被引入。

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/no-unneeded-ternary.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/no-unneeded-ternary.md)
