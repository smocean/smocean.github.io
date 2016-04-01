---
title: Rule space-before-blocks
layout: doc
translator: molee1905
proofreader: molee1905
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->

# Require Or Disallow Space Before Blocks (space-before-blocks)

# 要求或禁止块之前的空格 (space-before-blocks)

Consistency is an important part of any style guide.
While it is a personal preference where to put the opening brace of blocks,
it should be consistent across a whole project.
Having an inconsistent style distracts the reader from seeing the important parts of the code.

一致性是任何风格指南的重要组成部分。虽然在哪里放置块的开括号纯属个人偏好，但在整个项目中应该保持一致。不一致的风格将会分散读者阅读代码的注意力。

**Fixable:** This rule is automatically fixable using the `--fix` flag on the command line.

**Fixable:** 该规则可以通过`--fix`命令行进行自动修复。

## Rule Details

This rule will enforce consistency of spacing before blocks. It is only applied on blocks that don’t begin on a new line.

该规则将强制块之前的空格的一致性。它只在非行首的块上起作用。

* This rule ignores spacing which is between `=>` and a block. The spacing is handled by the `arrow-spacing` rule.

* 该规则忽略`=>`和块之间的空格。`arrow-spacing`规则处理这些空格。

* This rule ignores spacing which is between a keyword and a block. The spacing is handled by the `keyword-spacing` rule.

* 该规则忽略关键字和块之间的空格。`keyword-spacing`规则处理这些空格。

## Options

This rule takes one argument. If it is `"always"` then blocks must always have at least one preceding space. If `"never"` then all blocks should never have any preceding space. If different spacing is desired for function blocks, keyword blocks and classes, an optional configuration object can be passed as the rule argument to configure the cases separately.
( e.g. `{ "functions": "never", "keywords": "always", classes: "always" }` )

该规则有一个参数。如果为`"always"`，块语句必须总是至少有一个前置空格。如果为`"never"`，所有的块永远不会有前置空格。如果函数块和关键字块要求不同的空格类型，可以单独传递一个可选配置的对象作为该规则的参数来配置这种情况。(比如：`{ "functions": "never", "keywords": "always", classes: "always" } `)

The default is `"always"`.

默认为 `"always"`。

### "always"

The following patterns are considered problems:

以下模式被认为是有问题的：

```js
/*eslint space-before-blocks: 2*/

if (a){
    b();
}

function a(){}

for (;;){
    b();
}

try {} catch(a){}

class Foo{
  constructor(){}
}
```

The following patterns are not considered problems:

以下模式被认为是没有问题的：

```js
/*eslint space-before-blocks: 2*/

if (a) {
    b();
}

if (a) {
    b();
} else{ /*no error. this is checked by `keyword-spacing` rule.*/
    c();
}


function a() {}

for (;;) {
    b();
}

try {} catch(a) {}
```

### "never"

The following patterns are considered problems:

以下模式被认为是有问题的：

```js
/*eslint space-before-blocks: [2, "never"]*/

if (a) {
    b();
}

function a() {}

for (;;) {
    b();
}

try {} catch(a) {}
```

The following patterns are not considered problems:

以下模式被认为是没有问题的：

```js
/*eslint space-before-blocks: [2, "never"]*/

if (a){
    b();
}

function a(){}

for (;;){
    b();
}

try{} catch(a){}

class Foo{
  constructor(){}
}
```

The following patterns are considered problems when configured `{ "functions": "never", "keywords": "always", classes: "never" }`:

当配置为`{ "functions": "never", "keywords": "always", classes: "never" }`，以下模式被认为是有问题的：

```js
/*eslint space-before-blocks: [2, { "functions": "never", "keywords": "always", classes: "never" }]*/
/*eslint-env es6*/

function a() {}

try {} catch(a){}

class Foo{
  constructor() {}
}
```


The following patterns are not considered problems when configured `{ "functions": "never", "keywords": "always", classes: "never" }`:

当配置为`{ "functions": "never", "keywords": "always", classes: "never" }`，以下模式被认为是没有问题的：

```js
/*eslint space-before-blocks: [2, { "functions": "never", "keywords": "always", classes: "never" }]*/
/*eslint-env es6*/

for (;;) {
  // ...
}

describe(function(){
  // ...
});

class Foo {
  constructor(){}
}
```

The following patterns are considered problems when configured `{ "functions": "always", "keywords": "never", classes: "never" }`:

当配置为`{ "functions": "always", "keywords": "never", classes: "never" }`，以下模式被认为是有问题的：

```js
/*eslint space-before-blocks: [2, { "functions": "always", "keywords": "never", classes: "never" }]*/
/*eslint-env es6*/

function a(){}

try {} catch(a) {}

class Foo {
  constructor(){}
}
```


The following patterns are not considered problems when configured `{ "functions": "always", "keywords": "never", classes: "never" }`:

当配置为`{ "functions": "always", "keywords": "never", classes: "never" }`，以下模式被认为是没有问题的：

```js
/*eslint space-before-blocks: [2, { "functions": "always", "keywords": "never", classes: "never" }]*/
/*eslint-env es6*/

if (a){
  b();
}

var a = function() {}

class Foo{
  constructor() {}
}
```

The following patterns are considered problems when configured `{ "functions": "never", "keywords": "never", classes: "always" }`:

当配置为`{ "functions": "never", "keywords": "never", classes: "always" }`， 以下模式被认为是有问题的：

```js
/*eslint space-before-blocks: [2, { "functions": "never", "keywords": "never", classes: "always" }]*/
/*eslint-env es6*/

class Foo{
  constructor(){}
}
```


The following patterns are not considered problems when configured `{ "functions": "never", "keywords": "never", classes: "always" }`:

当配置为`{ "functions": "never", "keywords": "never", classes: "always" }`，以下模式被认为是没有问题的：

```js
/*eslint space-before-blocks: [2, { "functions": "never", "keywords": "never", classes: "always" }]*/
/*eslint-env es6*/

class Foo {
  constructor(){}
}
```

## When Not To Use It

You can turn this rule off if you are not concerned with the consistency of spacing before blocks or if you are using the `space-after-keywords` rule set to `"never"`.

如果你不关心块之前的空格的一致性或者你在使用`space-after-keywords`规则，而且设置了`"never"`，你可以关闭此规则。

## Related Rules

* [keyword-spacing](keyword-spacing)
* [arrow-spacing](arrow-spacing)
* [brace-style](brace-style)

## Version

This rule was introduced in ESLint 0.9.0.

该规则在 ESLint 0.9.0 中被引入。

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/space-before-blocks.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/space-before-blocks.md)
