---
title: Rule no-bitwise
layout: doc
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->
# Disallow Bitwise Operators (no-bitwise)

The use of bitwise operators in JavaScript is very rare and often `&` or `|` is simply a mistyped `&&` or `||`, which will lead to unexpected behavior.

```js
var x = y | z;
```

## Rule Details

This rule is aimed at catching typos that end up as bitwise operators, but are meant to be the much more common `&&`, '||', `<`, `>` operators. As such, it will warn whenever it encounters a bitwise operator:

The following patterns are considered problems:

```js
/*eslint no-bitwise: 2*/

var x = y | z;   /*error Unexpected use of '|'.*/

var x = y & z;   /*error Unexpected use of '&'.*/

var x = y ^ z;   /*error Unexpected use of '^'.*/

var x = ~ z;     /*error Unexpected use of '~'.*/

var x = y << z;  /*error Unexpected use of '<<'.*/

var x = y >> z;  /*error Unexpected use of '>>'.*/

var x = y >>> z; /*error Unexpected use of '>>>'.*/

x |= y;          /*error Unexpected use of '|='.*/

x &= y;          /*error Unexpected use of '&='.*/

x ^= y;          /*error Unexpected use of '^='.*/

x <<= y;         /*error Unexpected use of '<<='.*/

x >>= y;         /*error Unexpected use of '>>='.*/

x >>>= y;        /*error Unexpected use of '>>>='.*/
```

The following patterns are not considered problems:

```js
/*eslint no-bitwise: 2*/

var x = y || z;

var x = y && z;

var x = y > z;

var x = y < z;

x += y;
```

## Version

This rule was introduced in ESLint 0.0.2.

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/no-bitwise.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/no-bitwise.md)
