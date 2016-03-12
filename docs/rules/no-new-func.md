---
title: Rule no-new-func
layout: doc
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->

# Disallow Function Constructor (no-new-func)
# 禁止Function构造函数 (no-new-func)

It's possible to create functions in JavaScript using the `Function` constructor, such as:

在JavaScript中可以使用`Function`构造函数创建一个函数，例如：

```js
var x = new Function("a", "b", "return a + b");
```

This is considered by many to be a bad practice due to the difficult in debugging and reading these types of functions.

大多数人认为这是一个不好的实践，由于在调试和阅读这种类型函数上的困难。

## Rule Details

This error is raised to highlight the use of a bad practice. By passing a string to the Function constructor, you are requiring the engine to parse that string much in the way it has to when you call the eval function.

错误被引发用来标记不好实践的使用。通过将一个字符串传递到 Function 构造函数，当你调用 eval 函数，你要求引擎不得不过多的解析该字符串。

```js
/*eslint no-new-func: 2*/

var x = new Function("a", "b", "return a + b");
var x = Function("a", "b", "return a + b");
```

The following patterns are not considered problems:

以下模式被认为是没有问题的：

```js
/*eslint no-new-func: 2*/

var x = function (a, b) {
    return a + b;
};
```

## When Not To Use It

In more advanced cases where you really need to use the `Function` constructor.

在一些更高级的情况下，你真的需要使用`Function`构造函数。

## Further Reading

* [The Function constructor is eval](http://jslinterrors.com/the-function-constructor-is-eval/)

## Version

This rule was introduced in ESLint 0.0.7.

此规则在ESLint 0.0.7中被引入。

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/no-new-func.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/no-new-func.md)
