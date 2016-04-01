---
title: Rule no-implicit-coercion
layout: doc
translator: fengnana
proofreader: molee1905
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->

# Disallow the type conversion with shorter notations. (no-implicit-coercion)

# 禁止使用较短的符号实现类型转换 (no-implicit-coercion)

In JavaScript, there are a lot of different ways to convert value types.
Some of them might be hard to read and understand.

在 JavaScript 中，有许多不同的方式进行类型转换。其中有些可能难于阅读和理解。

Such as:

例如：

```js
var b = !!foo;
var b = ~foo.indexOf(".");
var n = +foo;
var n = 1 * foo;
var s = "" + foo;
foo += "";
```

Those can be replaced with the following code:

可以使用下面的代码替换:

```js
var b = Boolean(foo);
var b = foo.indexOf(".") !== -1;
var n = Number(foo);
var n = Number(foo);
var s = String(foo);
foo = String(foo);
```

## Rule Details

This rule is aimed to flag shorter notations for the type conversion, then suggest a more self-explanatory notation.

该规则目的就是标记出使用较短的符号进行类型转换的情况，建议使用一个更明确的符号。

## Options

This rule has three main options and one override option to allow some coercions as required.

该规则有三个主要选项和一个覆盖选项，覆盖选项允许一些强制要求。

```js
{
    "rules": {
        "no-implicit-coercion": [2, {
            "boolean": true,
            "number": true,
            "string": true,
            "allow": [/* "!!", "~", "*", "+" */]
        }]
    }
}
```

* `"boolean"` (`true` by default) - When this is `true`, this rule warns shorter type conversions for `boolean` type.

* `"boolean"`(默认是`true`)－当为`true`时，规则会对简短的`boolean`类型转换发出警告。

* `"number"` (`true` by default) - When this is `true`, this rule warns shorter type conversions for `number` type.

* `"number"`(默认是`true`)－当为`true`时，规则会对简短的`number`类型转换发出警告。

* `"string"` (`true` by default) - When this is `true`, this rule warns shorter type conversions for `string` type.

* `"string"`(默认是`true`)－当为`true`时，规则会对简短的`string`类型转换发出警告。

* `"allow"` (`empty` by default) - Each entry in this array can be one of `~`, `!!`, `+` or `*` that are to be allowed.

* `"allow"` (默认是`empty`) - 这个数组的每一项可以是 `~`，`!!`，`+` 或`*`。

Note that operator `+` in `allow` list would allow `+foo` (number coercion) as well as `"" + foo` (string coercion).

注意，在`allow`列表中，操作符`+`同时允许`+foo`（数字）和`"" + foo`(字符串)

### `boolean`

The following patterns are considered problems:

以下模式被认为是有问题的：

```js
/*eslint no-implicit-coercion: 2*/

var b = !!foo;
var b = ~foo.indexOf(".");
// only with `indexOf`/`lastIndexOf` method calling.

```

The following patterns are not considered problems:

以下模式被认为是没有问题的：

```js
/*eslint no-implicit-coercion: 2*/

var b = Boolean(foo);
var b = foo.indexOf(".") !== -1;

var n = ~foo; // This is a just binary negating.
```

### `number`

The following patterns are considered problems:

以下模式被认为是有问题的：

```js
/*eslint no-implicit-coercion: 2*/

var n = +foo;
var n = 1 * foo;
```

The following patterns are not considered problems:

以下模式被认为是没有问题的

```js
/*eslint no-implicit-coercion: 2*/

var b = Number(foo);
var b = parseFloat(foo);
var b = parseInt(foo, 10);
```

### `string`

The following patterns are considered problems:

以下模式被认为是有问题的：


```js
/*eslint no-implicit-coercion: 2*/

var n = "" + foo;

foo += "";
```

The following patterns are not considered problems:

以下模式被认为是没有问题的：

```js
/*eslint no-implicit-coercion: 2*/

var b = String(foo);
```

### Fine-grained control

Using `allow` list, we can override and allow specific operators.

当时使用`allow`列表，我们可以覆盖和允许指定的操作符。

For example, when the configuration is like this:

例如，当这样配置时：

```json
{
    "rules": {
        "no-implicit-coercion": [2, {
            "boolean": true,
            "number": true,
            "string": true,
            "allow": ["!!", "~"]
        }]
    }
}
```

The following patterns are not considered problems:

以下模式被认为是没有问题的：

```js
var b = !!foo;
var c = ~foo.indexOf(".");
```

## When Not To Use It

If you don't want to be notified about shorter notations for the type conversion, you can safely disable this rule.

如果你不想收到关于使用较短符号进行类型转换的通知，可以禁用此规则。

## Version

This rule was introduced in ESLint 1.0.0-rc-2.

此规则在 ESLint 1.0.0-rc-2 中被引入。

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/no-implicit-coercion.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/no-implicit-coercion.md)
