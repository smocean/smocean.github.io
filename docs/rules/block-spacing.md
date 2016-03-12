---
title: Rule block-spacing
layout: doc
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->

# Disallow or enforce spaces inside of single line blocks. (block-spacing)

# 禁止或强制在单行代码块中使用空格。 (block-spacing)

This rule is for spacing style within single line blocks.

该规则是关于单行代码块的间距风格的。

**Fixable:** This rule is automatically fixable using the `--fix` flag on the command line.

**Fixable:** 该规则可以通过`--fix`命令行进行自动修复。

## Rule Details

This rule is aimed to flag usage of spacing inside of blocks.

该规则旨在标示代码块中的空格的用法。

## Options

This rule has a option, its value is `"always"` or `"never"`.

该规则有个可选项, 值为 `"always"` 或 `"never"`。

- `"always"` (by default) enforces one or more spaces.

- `"always"` (默认) 强制是使用一个或多个空格。

- `"never"` disallows space(s).

- `"never"` 禁用空格。

### "always"

```json
{
  "block-spacing": [2, "always"]
}
```

The following patterns are considered problems:

以下模式被认为是有问题的：

```js
/*eslint block-spacing: 2*/
function foo() {return true;}
if (foo) { bar = 0;}
```

The following patterns are not considered problems:

以下模式被认为是没有问题的：

```js
/*eslint block-spacing: 2*/

function foo() { return true; }
if (foo) { bar = 0; }
```

### "never"

```json
{
  "block-spacing": [2, "never"]
}
```

The following patterns are considered problems:

以下模式被认为是有问题的：

```js
/*eslint block-spacing: [2, "never"]*/

function foo() { return true; }
if (foo) { bar = 0;}
```

The following patterns are not considered problems:

以下模式被认为是没有问题的：

```js
/*eslint block-spacing: [2, "never"]*/

function foo() {return true;}
if (foo) {bar = 0;}
```

## When Not To Use It

If you don't want to be notified about spacing style inside of blocks, you can safely disable this rule.

如果你不想收到单行代码块中间距风格问题的通知，你完全可以禁用此规则。

## Version

This rule was introduced in ESLint 1.2.0.

该规则在ESLint 1.2.0 被引入。

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/block-spacing.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/block-spacing.md)
