---
title: Rule padded-blocks
layout: doc
translator: molee1905
proofreader: molee1905
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->

# Enforce padding within blocks (padded-blocks)

# 强制块内填充 (padded-blocks)

Some style guides require block statements to start and end with blank lines. The goal is
to improve readability by visually separating the block content and the surrounding code.

一些风格指南要求块语句以空行开始并且以空行结束。目标是通过块内容和周围代码视觉上地分离来提高可读性。

```js
if (a) {

    b();

}
```

Since it's good to have a consistent code style, you should either always write
padded blocks or never do it.

代码风格统一是非常有好处的，你应总是写填充的块或永远不这么做。

## Rule Details

This rule enforces consistent padding within blocks.

该规则强制块内填充的一致性。

This rule takes one argument, which can be an string or an object. If it is `"always"` (the default) then block statements must start **and** end with a blank line. If `"never"`, then block statements should neither start nor end with a blank line. By default, this rule ignores padding in switch statements and classes.

该规则只有一个参数。可以是一个字符串或是一个对象。如果是`"always"`（默认），块语句必须以空行开始 **和**结束。如果为`"never"`，块语句不应以空行开始**或**结束。默认地，该规则忽略 switch 语句和 class 里的填充。

If you want to enforce padding within switches and classes, a configuration object can be passed as the rule argument to configure the cases separately ( e.g. `{ "blocks": "always", "switches": "always", "classes": "always" }` ).

如果你想强制在 switch 语句和 class 使用填充，可以传递一个配置对象，对其进行分别配置 (比如：`{ "blocks": "always", "switches": "always", "classes": "always" }`)。

The following patterns are considered problems when set to `"always"`:

当设置为`"always"`时，以下模式被认为是有问题的：

```js
/*eslint padded-blocks: [2, "always"]*/

if (a) {
    b();
}

if (a) { b(); }

if (a)
{
    b();
}

if (a) {

    b();
}

if (a) {
    b();

}

if (a) {
    // comment
    b();

}
```

The following patterns are not considered problems when set to `"always"`:

当设置为`"always"`时，以下模式被认为是没有问题的：

```js
/*eslint padded-blocks: [2, "always"]*/

if (a) {

    b();

}

if (a)
{

    b();

}

if (a) {

    // comment
    b();

}
```

The following patterns are considered problems when set to `"never"`:

当设置为`"never"`时，以下模式被认为是有问题的：

```js
/*eslint padded-blocks: [2, "never"]*/

if (a) {

    b();

}

if (a)
{

    b();

}

if (a) {

    b();
}

if (a) {
    b();

}
```

The following patterns are not considered problems when set to `"never"`:

当设置为`"never"`时，以下模式被认为是没有问题的：

```js
/*eslint padded-blocks: [2, "never"]*/

if (a) {
    b();
}

if (a)
{
    b();
}
```

The following patterns are considered problems when configured `{ "switches": "always" }`:

当配置为`{ "switches": "always" }`，以下模式被认为是有问题的：

```js
/*eslint padded-blocks: [2, { "switches": "always" }]*/

switch (a) {
    case 0: foo();
}
```

The following patterns are not considered problems when configured `{ "switches": "always" }`:

当配置为`{ "switches": "always" }`，以下模式被认为是没有问题的：

```js
/*eslint padded-blocks: [2, { "switches": "always" }]*/

switch (a) {

    case 0: foo();

}

if (a) {
    b();
}
```

The following patterns are considered problems when configured `{ "switches": "never" }`:

当配置为`{ "switches": "never" }`，以下模式被认为是有问题的：

```js
/*eslint padded-blocks: [2, { "switches": "never" }]*/

switch (a) {

    case 0: foo();

}
```

The following patterns are not considered problems when configured `{ "switches": "never" }`:

当配置为`{ "switches": "never" }`，以下模式被认为是没有问题的：

```js
/*eslint padded-blocks: [2, { "switches": "never" }]*/

switch (a) {
    case 0: foo();
}

if (a) {

    b();

}
```

The following patterns are considered problems when configured `{ "classes": "always" }`:

当配置为`{ "classes": "always" }`，以下模式被认为是有问题的：

```js
/*eslint padded-blocks: [2, { "classes": "always" }]*/

class  A {
    constructor(){
    }
}
```

The following patterns are not considered problems when configured `{ "classes": "always" }`:

当配置为`{ "classes": "always" }`，以下模式被认为是没有问题的：

```js
/*eslint padded-blocks: [2, { "classes": "always" }]*/

class  A {

    constructor(){
    }

}
```

The following patterns are considered problems when configured `{ "classes": "never" }`:

当配置为`{ "classes": "never" }`，以下模式被认为是有问题的：

```js
/*eslint padded-blocks: [2, { "classes": "never" }]*/

class  A {

    constructor(){
    }

}
```

The following patterns are not considered problems when configured `{ "classes": "never" }`:

当配置为`{ "classes": "never" }`，以下模式被认为是没有问题的：

```js
/*eslint padded-blocks: [2, { "classes": "never" }]*/

class  A {
    constructor(){
    }
}
```

## When Not To Use It

You can turn this rule off if you are not concerned with the consistency of padding within blocks.

如果你并不关心块内填充的一致性，你可以关闭此规则。

## Version

This rule was introduced in ESLint 0.9.0.

该规则在 ESLint 0.9.0 中被引入。

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/padded-blocks.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/padded-blocks.md)
