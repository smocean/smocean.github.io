---
title: Rule guard-for-in
layout: doc
translator: fengnana
proofreader: molee1905
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->

# Require Guarding for-in (guard-for-in)

# 需要约束for-in (guard-for-in)

Looping over objects with a `for in` loop will include properties that are inherited through the prototype chain. This behavior can lead to unexpected items in your "for" loop.

在使用`for in`循环变量对象时，会把从原型链继承来的属性也包括进来。这样会遍历到不是你想要的项。

```js
for (key in foo) {
    doSomething(key);
}
```

## Rule Details

This rule is aimed at preventing unexpected behavior that could arise from using a `for in` loop without filtering the results in the loop. As such, it will warn when `for in` loops do not filter their results with an `if` statement.

此规则目的在于，阻止在`for in`遍历过程中，由于不对结果进行筛选而导致意想不到的行为发生。因此，当`for in`循环中，没有使用`if` 语句对结果进行筛选时，该规则将会发出警告。

The following patterns are considered problems:

以下模式被认为是有问题的：

```js
/*eslint guard-for-in: 2*/

for (key in foo) {
    doSomething(key);
}
```

The following patterns are not considered problems:

以下模式被认为是没有问题的：

```js
/*eslint guard-for-in: 2*/

for (key in foo) {
    if ({}.hasOwnProperty.call(foo, key)) {
        doSomething(key);
    }
}
```

## Further Reading

* [Exploring JavaScript for-in loops](http://javascriptweblog.wordpress.com/2011/01/04/exploring-javascript-for-in-loops/)
* [The pitfalls of using objects as maps in JavaScript](http://www.2ality.com/2012/01/objects-as-maps.html)

## Version

This rule was introduced in ESLint 0.0.6.

此规则在 ESLint 0.0.6 中被引入。

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/guard-for-in.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/guard-for-in.md)
