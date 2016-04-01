---
title: Rule no-class-assign
layout: doc
translator: molee1905
proofreader: molee1905
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->

# Disallow modifying variables of class declarations (no-class-assign)

# 不允许修改类声明的变量 (no-class-assign)

`ClassDeclaration` creates a variable, and we can modify the variable.

`ClassDeclaration` 创建一个变量，我们可以修改这个变量。

```js
/*eslint-env es6*/

class A { }
A = 0;
```

But the modification is a mistake in most cases.

但是在大多数情况下，这样的修改是个错误。

## Rule Details

This rule is aimed to flag modifying variables of class declarations.

该规则旨在标记类声明中变量的修改情况。

The following patterns are considered problems:

以下模式被认为是有问题的：

```js
/*eslint no-class-assign: 2*/
/*eslint-env es6*/

class A { }
A = 0;
```

```js
/*eslint no-class-assign: 2*/
/*eslint-env es6*/

A = 0;
class A { }
```

```js
/*eslint no-class-assign: 2*/
/*eslint-env es6*/

class A {
    b() {
        A = 0;
    }
}
```

```js
/*eslint no-class-assign: 2*/
/*eslint-env es6*/

let A = class A {
    b() {
        A = 0;
        // `let A` is shadowed by the class name.
    }
}
```

The following patterns are not considered problems:

以下模式被认为是没有问题的：

```js
/*eslint no-class-assign: 2*/
/*eslint-env es6*/

let A = class A { }
A = 0; // A is a variable.
```

```js
/*eslint no-class-assign: 2*/
/*eslint-env es6*/

let A = class {
    b() {
        A = 0; // A is a variable.
    }
}
```

```js
/*eslint no-class-assign: 2*/
/*eslint-env es6*/

class A {
    b(A) {
        A = 0; // A is a parameter.
    }
}
```

## When Not To Use It

If you don't want to be notified about modifying variables of class declarations, you can safely disable this rule.

如果你不想收到类声明中变量的修改的通知，你可以禁用此规则。

## Version

This rule was introduced in ESLint 1.0.0-rc-1.

该规则在 ESLint 1.0.0-rc-1 中被引入。

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/no-class-assign.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/no-class-assign.md)
