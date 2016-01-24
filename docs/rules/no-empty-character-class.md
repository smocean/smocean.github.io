---
title: Rule no-empty-character-class
layout: doc
translator: ybbjegj
proofreader: molee1905
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->
# Disallow Empty Character Classes (no-empty-character-class)

# 禁止空字符集（no-empty-character-class）

Empty character classes in regular expressions do not match anything and can result in code that may not work as intended.

在正则表达式中空字符集不能匹配任何字符，还可能导致代码不能按预期工作。

```js
var foo = /^abc[]/;
```

## Rule Details

This rule is aimed at highlighting possible typos and unexpected behavior in regular expressions which may arise from the use of empty character classes.

该规则旨在强调正则表达式中使用空字符集时，可能出现的拼写错误和异常行为。

The following patterns are considered problems:

以下模式被认为是有问题的：

```js
/*eslint no-empty-character-class: 2*/

var foo = /^abc[]/;  /*error Empty class.*/

/^abc[]/.test(foo);  /*error Empty class.*/

bar.match(/^abc[]/); /*error Empty class.*/
```

The following patterns are not considered problems:

以下模式被认为是没有问题的：

```js
/*eslint no-empty-character-class: 2*/

var foo = /^abc/;

var foo = /^abc[a-z]/;

var bar = new RegExp("^abc[]");
```

## Related Rules

* [no-empty-class](no-empty-class) (removed)

## Version

This rule was introduced in ESLint 0.22.0.

该规则在 ESLint 0.22.0 中被引入。

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/no-empty-character-class.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/no-empty-character-class.md)
