---
title: Rule no-multi-str
layout: doc
translator: fengnana
proofreader: molee1905
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->

# Disallow Multiline Strings (no-multi-str)

# 禁止多行字符串 (no-multi-str)

It's possible to create multiline strings in JavaScript by using a slash before a newline, such as:

在 JavaScript 中，可以在新行之前使用斜线创建多行字符串，例如：

```js
var x = "Line 1 \
         Line 2";
```

Some consider this to be a bad practice as it was an undocumented feature of JavaScript that was only formalized later.

一些人认为这不是一个好的做法，因为它是 JavaScript 中的一个非正式的特性。

## Rule Details

This rule is aimed at preventing the use of multiline strings.

该规则是为了防止多行字符串的使用。

The following generates a warning:

下面的模式会发出一个警告：

```js
/*eslint no-multi-str: 2*/ 
var x = "Line 1 \
         Line 2";
```

The following does not generate a warning:

下面的模式不会发出警告：

```js
/*eslint no-multi-str: 2*/

var x = "Line 1\n" +
        "Line 2";
```


## Further Reading

* [Bad escapement of EOL](http://jslinterrors.com/bad-escapement-of-eol-use-option-multistr-if-needed/)

## Version

This rule was introduced in ESLint 0.0.9.

此规则在 ESLint 0.0.9 中被引入。

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/no-multi-str.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/no-multi-str.md)
