---
title: Rule no-alert
layout: doc
translator: fengnana
proofreader: molee1905
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->

# Disallow Use of Alert (no-alert)

# 禁用 Alert (no-alert)

JavaScripts' alert, confirm, and prompt functions are widely considered to be obtrusive as UI elements and should be replaced by a more appropriate custom UI implementation. Furthermore, alert is often used while debugging code, which should be removed before deployment to production.

JavaScript的 alert，confirm，和 prompt 功能被广泛认为是突兀的 UI 元素，应该被一个更合适的自定义的 UI 界面代替。此外, alert 经常被用于调试代码，部署到生产环境之前应该删除。

```js
alert("here!");
```

## Rule Details

This rule is aimed at catching debugging code that should be removed and popup UI elements that should be replaced with less obtrusive, custom UIs. As such, it will warn when it encounters `alert`, `prompt`, and `confirm` function calls which are not shadowed.

此规则目的在于捕获本应被移除的调试代码和应该被替换为不突兀的、自定义用户界面的弹出式UI元素。因此，它会给出警告，当意外碰到`alert`， `prompt`，和 `confirm`不会被追踪的函数调用。

该规则旨在捕获本应移除的调试代码和应该被替换为不那么突兀的 UI 元素。因此，当遇到`alert`，`prompt`和`confirm`时，该规则将发出警告。

The following patterns are considered problems:

以下模式被认为是有问题的：

```js
/*eslint no-alert: 2*/

alert("here!");

confirm("Are you sure?");

prompt("What's your name?", "John Doe");
```

The following patterns are not considered problems:

以下模式被认为是没有问题的：

```js
/*eslint no-alert: 2*/

customAlert("Something happened!");

customConfirm("Are you sure?");

customPrompt("Who are you?");

function foo() {
    var alert = myCustomLib.customAlert;
    alert();
}
```

## Related Rules

* [no-console](no-console)
* [no-debugger](no-debugger)

## Version

This rule was introduced in ESLint 0.0.5.

此规则在 ESLint 0.0.5 中被引入。

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/no-alert.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/no-alert.md)
