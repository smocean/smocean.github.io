---
title: Rule no-invalid-this
layout: doc
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->

# Disallow `this` keywords outside of classes or class-like objects. (no-invalid-this)
# 禁止`this`关键字在类或者类对象之外出现 (no-invalid-this)

Under the strict mode, `this` keywords outside of classes or class-like objects might be `undefined` and raise a `TypeError`.

在严格模式下，类或者类似类对象之外的`this`关键字也许会是`undefined`并且引起一个`TypeError`。

## Rule Details

This rule aims to flag usage of `this` keywords outside of classes or class-like objects.

此规则目的在于标记类或者类似类对象之外的`this`关键字的使用。

Basically this rule checks whether or not a function which are containing `this` keywords is a constructor or a method.

基本上该规则检查一个包含`this`关键字的函数是否是一个构造器或者一个方法。

This rule judges from following conditions whether or not the function is a constructor:

此规则从以下条件中判断函数是否是一个构造函数。

* The name of the function starts with uppercase.

* 函数的名字以大写字母开头。

* The function is a constructor of ES2015 Classes.

* 函数是ES2015类构造函数。

This rule judges from following conditions whether or not the function is a method:

此规则从以下条件中判断函数是否是一个方法。

* The function is on an object literal.

* 函数在对象字面量上

* The function assigns to a property.

* 函数作为属性

* The function is a method/getter/setter of ES2015 Classes. (excepts static methods)

* 函数是一个ES2015类的 方法/getter/setter.(除静态方法)

And this rule allows `this` keywords in functions below:

此规则允许以下函数中的`this`关键字：

* The `call/apply/bind` method of the function is called directly.

* 函数的 `call/apply/bind` 方法被直接调用。

* The function is a callback of array methods (such as `.forEach()`) if `thisArg` is given.

* 如果给出`thisArg`，函数是数组方法的一个回调（比如`.forEach()`）

* The function has `@this` tag in its JSDoc comment.

* 函数在JSDoc注释标记中有`@this`标签。

Otherwise are considered problems.

其他情况被认为是有问题的。
 

This rule warns below **only** under the strict mode.
Please note your code in ES2015 Modules/Classes is always the strict mode.

此规则**只**在严格模式下给出警告。请注意你的代码在ES2015模块/类总是严格的模式。

The following patterns are considered problems:

以下模式被认为是有问题的：

```js
/*eslint no-invalid-this: 2*/
/*eslint-env es6*/

this.a = 0;
baz(() => this);

(function() {
    this.a = 0;
    baz(() => this);
})();

function foo() {
    this.a = 0;
    baz(() => this);
}

var foo = function() {
    this.a = 0;
    baz(() => this);
};

foo(function() {
    this.a = 0;
    baz(() => this);
});

obj.foo = () => {
    // `this` of arrow functions is the outer scope's.
    this.a = 0;
};

var obj = {
    aaa: function() {
        return function foo() {
            // There is in a method `aaa`, but `foo` is not a method.
            this.a = 0;
            baz(() => this);
        };
    }
};

foo.forEach(function() {
    this.a = 0;
    baz(() => this);
});
```

The following patterns are not considered problems:

以下模式被认为是没有问题的：

```js
/*eslint no-invalid-this: 2*/
/*eslint-env es6*/

function Foo() {
    // OK, this is in a legacy style constructor.
    this.a = 0;
    baz(() => this);
}

class Foo {
    constructor() {
        // OK, this is in a constructor.
        this.a = 0;
        baz(() => this);
    }
}

var obj = {
    foo: function foo() {
        // OK, this is in a method (this function is on object literal).
        this.a = 0;
    }
};

var obj = {
    foo() {
        // OK, this is in a method (this function is on object literal).
        this.a = 0;
    }
};

var obj = {
    get foo() {
        // OK, this is in a method (this function is on object literal).
        return this.a;
    }
};

var obj = Object.create(null, {
    foo: {value: function foo() {
        // OK, this is in a method (this function is on object literal).
        this.a = 0;
    }}
});

Object.defineProperty(obj, "foo", {
    value: function foo() {
        // OK, this is in a method (this function is on object literal).
        this.a = 0;
    }
});

Object.defineProperties(obj, {
    foo: {value: function foo() {
        // OK, this is in a method (this function is on object literal).
        this.a = 0;
    }}
});

function Foo() {
    this.foo = function foo() {
        // OK, this is in a method (this function assigns to a property).
        this.a = 0;
        baz(() => this);
    };
}

obj.foo = function foo() {
    // OK, this is in a method (this function assigns to a property).
    this.a = 0;
};

Foo.prototype.foo = function foo() {
    // OK, this is in a method (this function assigns to a property).
    this.a = 0;
};

class Foo {
    foo() {
        // OK, this is in a method.
        this.a = 0;
        baz(() => this);
    }

    static foo() {
        // OK, this is in a method (static methods also have valid this).
        this.a = 0;
        baz(() => this);
    }
}

var foo = (function foo() {
    // OK, the `bind` method of this function is called directly.
    this.a = 0;
}).bind(obj);

foo.forEach(function() {
    // OK, `thisArg` of `.forEach()` is given.
    this.a = 0;
    baz(() => this);
}, thisArg);

/** @this Foo */
function foo() {
    // OK, this function has a `@this` tag in its JSDoc comment.
    this.a = 0;
}
```

## When Not To Use It

If you don't want to be notified about usage of `this` keyword outside of classes or class-like objects, you can safely disable this rule.

如果你不想得到通知，关于`this`关键字在类或者类似类对象之外使用，你可以安全的关闭此规则。

## Version

This rule was introduced in ESLint 1.0.0-rc-2.

此规则在ESLint 1.0.0-rc-2中被引入。

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/no-invalid-this.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/no-invalid-this.md)
