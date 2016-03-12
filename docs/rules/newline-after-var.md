---
title: Rule newline-after-var
layout: doc
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->

# Require or disallow an empty newline after variable declarations (newline-after-var)

# 要求或禁止变量声明语句后的空行 (newline-after-var)

As of today there is no consistency in separating variable declarations from the rest of the code. Some developers leave an empty line between var statements and the rest of the code like:

目前，变量声明和其余代码如何分开并没有一致性。以下开发者在两者之间保留一行空行，如下：

```js
var foo;

// do something with foo
```

Whereas others don't leave any empty newlines at all.

然而其他人并不这样做。

```js
var foo;
// do something with foo
```

The problem is when these developers work together in a project. This rule enforces a coding style where empty newlines are allowed or disallowed after `var`, `let`, or `const` statements. It helps the code to look consistent across the entire project.

在一个项目中，这些开发者在一起工作时就成了问题。该规则强制使用一种代码风格，即`var`，`let`, 或 `const`语句之后是否允许有空行。它有助于整个项目的代码看起来是一致的。

## Rule Details

This rule enforces a coding style where empty newlines are required or disallowed after `var`, `let`, or `const` statements to achieve a consistent coding style across the project.

## Options

This rule takes one option, a string, which can be:

* `"always"` enforces empty newlines after `var`, `let` or `const` (default)
* `"never"` disallows empty newlines after `var`, `let` or `const`

该规则强制一种代码风格，即`var`，`let`, 或 `const`语句之后是否允许有空行，使整个项目代码风格统一。
除了`always` 和 `never`，其他可选项值均为无效，默认为`always`。

The following patterns are considered problems:

以下模式被认为是有问题的：

```js
/*eslint newline-after-var: [2, "always"]*/

var greet = "hello,",
    name = "world";
console.log(greet, name);
```

```js
/*eslint newline-after-var: [2, "never"]*/
/*eslint-env es6*/

let greet = "hello,",
    name = "world";

console.log(greet, name);
```

```js
/*eslint newline-after-var: 2*/  // defaults to always
/*eslint-env es6*/

var greet = "hello,";
const NAME = "world";
console.log(greet, NAME);
```

The following patterns are not considered problems:

以下模式被认为是没有问题的：

```js
/*eslint newline-after-var: [2, "always"]*/

var greet = "hello,",
    name = "world";

console.log(greet, name);
```

```js
/*eslint newline-after-var: [2, "never"]*/
/*eslint-env es6*/

let greet = "hello,",
    name = "world";
console.log(greet, name);
```

```js
/*eslint newline-after-var: 2*/  // defaults to always
/*eslint-env es6*/

var greet = "hello,";
const NAME = "world";

console.log(greet, NAME);
```

Note: in `"always"` mode, comments on a line directly after var statements are treated like additional var statements.
That is, they do not require a blank line between themselves and the var statements above, but do require a blank line after them.

注意：在 `"always"`模式中，var语句后紧随的注释被让当作额外的var语句。
这就是为什么，它们不要求在它们和上面的var语句之间有空行，而要求在它们之后有一空行。

The following patterns are considered problems:

以下模式被认为是有问题的：

```js
/*eslint newline-after-var: [2, "always"]*/

var greet = "hello,";
var name = "world";
// var name = require("world");
console.log(greet, name);


/*eslint-disable camelcase*/
var greet = "hello,";
var target_name = "world";
/*eslint-enable camelcase*/
console.log(greet, name);
```

The following patterns are not considered problems:

以下模式被认为是没有问题的：

```js
/*eslint newline-after-var: [2, "always"]*/

var greet = "hello,";
var name = "world";
// var name = require("world");

console.log(greet, name);


/*eslint-disable camelcase*/
var greet = "hello,";
var target_name = "world";
/*eslint-enable camelcase*/

console.log(greet, name);
```

## Version

This rule was introduced in ESLint 0.18.0.

该规则在ESLint 0.18.0 中被引入。

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/newline-after-var.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/newline-after-var.md)
