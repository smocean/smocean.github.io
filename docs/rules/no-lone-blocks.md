---
title: Rule no-lone-blocks
layout: doc
translator: fengnana
proofreader: molee1905
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->

# Disallow Unnecessary Nested Blocks (no-lone-blocks)

# 禁用不必要的嵌套块 (no-lone-blocks)

In JavaScript, prior to ES6, standalone code blocks delimited by curly braces do not create a new scope and have no use. For example, these curly braces do nothing to `foo`:

在 JavaScript 中，ES6 之前，由花括号分隔开的独立代码块不会创建新的作用域，也就不起什么作用。例如，这些花括号对`foo`不起任何作用：

```js
{
    var foo = bar();
}
```

In ES6, code blocks may create a new scope if a block-level binding (`let` and `const`), a class declaration or a function declaration (in strict mode) are present. A block is not considered redundant in these cases.

在 ES6 中，如果出现一个块级绑定 (`let`和`const`)，类声明或函数声明（在严格模式下），代码块就会创建一个新的作用域。在这些情况下，代码块不会被认为是多余的。

## Rule Details

This rule aims to eliminate unnecessary and potentially confusing blocks at the top level of a script or within other blocks.

该规则旨在消除脚本顶部或其它块中不必要的和潜在的令人困惑的代码块。

The following patterns are considered problems:

以下默认被认为是有问题的：

```js
/*eslint no-lone-blocks: 2*/

{}

if (foo) {
    bar();
    {
        baz();
    }
}

function bar() {
    {
        baz();
    }
}

{
    function foo() {}
}
```

The following patterns are not considered problems:

以下模式被认为是没有问题的：

```js
/*eslint-env es6*/
/*eslint no-lone-blocks: 2*/

while (foo) {
    bar();
}

if (foo) {
    if (bar) {
        baz();
    }
}

function bar() {
    baz();
}

{
    let x = 1;
}

{
    const y = 1;
}

{
    class Foo {}
}
```

In strict mode, with `ecmaFeatures: { blockBindings: true }`, the following will not warn:

在严格模式下，设置 `ecmaFeatures: { blockBindings: true }`，以下的模式不会发出警告：

```js
/*eslint-env es6*/
/*eslint no-lone-blocks: 2*/
"use strict";

{
    function foo() {}
}
```

## Version

This rule was introduced in ESLint 0.4.0.

此规则在 ESLint 0.4.0 中被引入。

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/no-lone-blocks.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/no-lone-blocks.md)
