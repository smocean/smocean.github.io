---
title: Rule prefer-const
layout: doc
translator: molee1905
proofreader: summart
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->

# Suggest using `const` (prefer-const)

# 建议使用`const` (prefer-const)

If a variable is never reassigned, using the `const` declaration is better.

如果一个变量不会被重新赋值，最好使用`const`进行声明。

`const` declaration tells readers, "this variable is never reassigned," reducing cognitive load and improving maintainability.

`const`声明告诉读者，“这个变量从不会被重新赋值”，从而减少认知负荷，提高可维护性。

## Rule Details

This rule is aimed at flagging variables that are declared using `let` keyword, but never reassigned after the initial assignment.

该规则旨在标记那些使用`let`声明，但在初始化赋值后从未被修改过的变量。

Examples of **incorrect** code for this rule:

**错误**代码示例：

```js
/*eslint prefer-const: "error"*/
/*eslint-env es6*/

// it's initialized and never reassigned.
let a = 3;
console.log(a);

let a;
a = 0;
console.log(a);

// `i` is redefined (not reassigned) on each loop step.
for (let i in [1, 2, 3]) {
    console.log(i);
}

// `a` is redefined (not reassigned) on each loop step.
for (let a of [1, 2, 3]) {
    console.log(a);
}

// the initializer is separated.
let a;
a = 0;
console.log(a);
```

Examples of **correct** code for this rule:

**正确**代码示例：

```js
/*eslint prefer-const: "error"*/
/*eslint-env es6*/

// using const.
const a = 0;

// it's never initialized.
let a;
console.log(a);

// it's reassigned after initialized.
let a;
a = 0;
a = 1;
console.log(a);

// it's initialized in a different block from the declaration.
let a;
if (true) {
    a = 0;
}
console.log(a);

// it's initialized at a place that we cannot write a variable declaration.
let a;
if (true) a = 0;
console.log(a);

// `i` gets a new binding each iteration
for (const i in [1, 2, 3]) {
  console.log(i);
}

// `a` gets a new binding each iteration
for (const a of [1, 2, 3]) {
  console.log(a);
}

// `end` is never reassigned, but we cannot separate the declarations without modifying the scope.
for (let i = 0, end = 10; i < end; ++i) {
    console.log(a);
}

// the initializer is located at another block.
let a;
if (true) {
    a = 0;
}
console.log(a);

// suggest to use `no-var` rule.
var b = 3;
console.log(b);
```

## Options

```json
{
    "prefer-const": ["error", {"destructuring": "any"}]
}
```

### destructuring

The kind of the way to address variables in destructuring.

在解构中有多种方式处理变量。

There are 2 values:

有 2 个值：

* `"any"` (default) - If any variables in destructuring should be `const`, this rule warns for those variables.
* `"any"` (默认) - 在解构中，任何变量都应该是`const`，该规则将发出警告。
* `"all"` - If all variables in destructuring should be `const`, this rule warns the variables. Otherwise, ignores them.
* `"all"` - 在解构中，所有变量都应该是`const`，该规则将发出警告。否则，忽略它们。

Examples of **incorrect** code for the default `{"destructuring": "any"}` option:

默认选项`{"destructuring": "any"}`的 **错误**代码示例：

```js
/*eslint prefer-const: "error"*/
/*eslint-env es6*/

let {a, b} = obj;    /*error 'b' is never reassigned, use 'const' instead.*/
a = a + 1;
```

Examples of **correct** code for the default `{"destructuring": "any"}` option:

默认选项`{"destructuring": "any"}`的 **正确**代码示例：

```js
/*eslint prefer-const: "error"*/
/*eslint-env es6*/

// using const.
const {a: a0, b} = obj;
const a = a0 + 1;

// all variables are reassigned.
let {a, b} = obj;
a = a + 1;
b = b + 1;
```

Examples of **incorrect** code for the `{"destructuring": "all"}` option:

`{"destructuring": "all"}`选项的 **错误**代码示例：

```js
/*eslint prefer-const: ["error", {"destructuring": "all"}]*/
/*eslint-env es6*/

// all of `a` and `b` should be const, so those are warned.
let {a, b} = obj;    /*error 'a' is never reassigned, use 'const' instead.
                             'b' is never reassigned, use 'const' instead.*/
```

Examples of **correct** code for the `{"destructuring": "all"}` option:

`{"destructuring": "all"}`选项的 **正确**代码示例：

```js
/*eslint prefer-const: ["error", {"destructuring": "all"}]*/
/*eslint-env es6*/

// 'b' is never reassigned, but all of `a` and `b` should not be const, so those are ignored.
let {a, b} = obj;
a = a + 1;
```

## When Not To Use It

If you don't want to be notified about variables that are never reassigned after initial assignment, you can safely disable this rule.

如果你不想被通知哪些变量初始化赋值后再没有被修改过，禁用此规则即可。

## Related Rules

* [no-var](no-var)

## Version

This rule was introduced in ESLint 0.23.0.

该规则在 ESLint 0.23.0 中被引入。

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/prefer-const.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/prefer-const.md)
