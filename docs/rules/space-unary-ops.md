---
title: Rule space-unary-ops
layout: doc
translator: molee1905
proofreader: molee1905
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->

# Require or disallow spaces before/after unary operators (space-unary-ops)

# 要求或禁止在一元操作符之前或之后存在空格 (space-unary-ops)

Some style guides require or disallow spaces before or after unary operators. This is mainly a stylistic issue, however, some JavaScript expressions can be written without spacing which makes it harder to read and maintain.

一些风格指南要求或禁止在一元操作符之前或之后存在空格。这主要是一个风格问题，然而，一些Javascript表达式如果不写空格将会使其难以阅读和维护。

**Fixable:** This rule is automatically fixable using the `--fix` flag on the command line.

**Fixable:** 该规则可以通过`--fix`命令行进行自动修复。

## Rule Details

This rule enforces consistency regarding the spaces after `words` unary operators and after/before `nonwords` unary operators.

该规则强制`words`一元操作符后空格和`nonwords`一元操作符之前或之后的空格的一致性。

Examples of unary `words` operators:

一元`words`操作符的例子：

```js
// new
var joe = new Person();

// delete
var obj = {
    foo: 'bar'
};
delete obj.foo;

// typeof
typeof {} // object

// void
void 0 // undefined
```

Examples of unary `nonwords` operators:

一元`nonwords`操作符的例子：

```js
if ([1,2,3].indexOf(1) !== -1) {};
foo = --foo;
bar = bar++;
baz = !foo;
qux = !!baz;
```

## Options

This rule has two options: `words` and `nonwords`:

该规则有两个可选项：`words` 和 `nonwords`：

* `words` - applies to unary word operators such as: `new`, `delete`, `typeof`, `void`, `yield`

* `words` - 适用于单词类一元操作符，例如： `new`， `delete`， `typeof`， `void`， `yield`

* `nonwords` - applies to unary operators such as: `-`, `+`, `--`, `++`, `!`, `!!`

* `nonwords` - 适用于这些一元操作符: `-`, `+`, `--`, `++`, `!`, `!!`

Given the default values `words`: `true`, `nonwords`: `false`, the following patterns are considered problems:

使用默认设置 `words`: `true`, `nonwords`: `false`， 以下模式被认为是有问题的：

```js
/*eslint space-unary-ops: 2*/

typeof!foo;

void{foo:0};

new[foo][0];

delete(foo.bar);

++ foo;

foo --;

- foo;

+ "3";
```

```js
/*eslint space-unary-ops: 2*/
/*eslint-env es6*/

function *foo() {
    yield(0)
}
```

Given the default values `words`: `true`, `nonwords`: `false`, the following patterns are not considered problems:

使用默认设置 `words`: `true`, `nonwords`: `false`， 以下模式被认为是没有问题的：

```js
/*eslint space-unary-ops: 2*/

// Word unary operator "delete" is followed by a whitespace.
delete foo.bar;

// Word unary operator "new" is followed by a whitespace.
new Foo;

// Word unary operator "void" is followed by a whitespace.
void 0;

// Unary operator "++" is not followed by whitespace.
++foo;

// Unary operator "--" is not preceded by whitespace.
foo--;

// Unary operator "-" is not followed by whitespace.
-foo;

// Unary operator "+" is not followed by whitespace.
+"3";
```

```js
/*eslint space-unary-ops: 2*/
/*eslint-env es6*/

function *foo() {
    yield (0)
}
```

## Version

This rule was introduced in ESLint 0.10.0.

该规则在 ESLint 0.10.0 中被引入。

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/space-unary-ops.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/space-unary-ops.md)
