---
title: Rule no-proto
layout: doc
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->

# Disallow Use of `__proto__` (no-proto)

# 禁止使用`__proto__`（no-proto）

`__proto__` property has been deprecated as of ECMAScript 3.1 and shouldn't be used in the code.Use `getPrototypeOf` method instead.

`__proto__`属性在ECMAScript 3.1中已经被弃用并且不会在代码中被使用。使用`getPrototypeOf`方法替代`__proto__`。

## Rule Details

When an object is created `__proto__` is set to the original prototype property of the object’s constructor function. `getPrototypeOf` is the preferred method of getting "the prototype".

当一个对象被创建时，`__proto__`被设置为对象的原始原型属性构造方法。`getPrototypeOf`是获取"the prototype"的首选方法。

The following patterns are considered problems:

以下模式被认为是有问题的：

```js
/*eslint no-proto: 2*/

var a = obj.__proto__;

var a = obj["__proto__"];
```

The following patterns are considered okay and could be used alternatively:

以下模式被认为是没有问题的，并且可以做为备选方案：

```js
/*eslint no-proto: 2*/

var a = Object.getPrototypeOf(obj);
```

## When Not To Use It

If you need to support legacy browsers, you might want to turn this rule off, since support for `getPrototypeOf` is not yet universal.

如果你需要支持老版本的浏览器，你可能会想要关闭此规则，因为`getPrototypeOf`还没有被广泛支持。

## Further Reading

* [Object.getPrototypeOf](http://ejohn.org/blog/objectgetprototypeof/)

## Version

This rule was introduced in ESLint 0.0.9.

此规则在ESLint 0.0.9中被引入。

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/no-proto.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/no-proto.md)
