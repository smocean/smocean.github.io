---
title: Rule no-sequences
layout: doc
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->

# Disallow Use of the Comma Operator (no-sequences)

# 不允许使用逗号操作符 (no-sequences)

The comma operator includes multiple expressions where only one is expected. It evaluates each operand from left to right and returns the value of the last operand. However, this frequently obscures side effects, and its use is often an accident. Here are some examples of its use:

逗号操作符包含的多个表达式只有一个是预期的。从左到右评估每一个操作数并且返回最后一个操作数的值。然而，它经常引起副作用，并且它的使用经常是个意外。这里有几个使用例子：

```js
var a = (3, 5); // a = 5

a = b += 5, a + b;

while (a = next(), a && a.length);

(0,eval)("doSomething();");
```

## Rule Details

This rule forbids the use of the comma operator, with the following exceptions:

此规则禁止逗号操作符的使用，以下情况除外：

* In the initialization or update portions of a `for` statement.

在初始化或者`for`语句更新选项时。

* If the expression sequence is explicitly wrapped in parentheses.

如果表达式顺序被显示的括号包裹。

The following patterns are considered problems:

以下模式被认为是有问题的：

```js
/*eslint no-sequences: 2*/

foo = doSomething, val;

do {} while (doSomething(), !!test);

for (; doSomething(), !!test; );

if (doSomething(), !!test);

switch (val = foo(), val) {}

while (val = foo(), val < 42);

with (doSomething(), val) {}
```

The following patterns are not considered problems:

以下问题被认为是没有问题的：

```js
/*eslint no-sequences: 2*/

foo = (doSomething(), val);

(0,eval)("doSomething();");

do {} while ((doSomething(), !!test));

for (i = 0, j = 10; i < j; i++, j--);

if ((doSomething(), !!test));

switch ((val = foo(), val)) {}

while ((val = foo(), val < 42));

// with ((doSomething(), val)) {}
```

## When Not To Use It

Disable this rule if sequence expressions with the comma operator are acceptable.

如果逗号操作符在有序的表达式中使用是可接受的，禁用此规则。

## Version

This rule was introduced in ESLint 0.5.1.

此规则在ESLint 0.5.1中被引入。

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/no-sequences.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/no-sequences.md)
