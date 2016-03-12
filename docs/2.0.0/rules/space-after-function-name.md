---
title: Rule space-after-function-name
layout: doc
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->
# Require or disallow spaces following function names (space-after-function-name)

**Replacement notice**: This rule was removed in ESLint v1.0 and replaced by the [space-before-function-paren](space-before-function-paren) rule.

Whitespace between a function name and its parameter list is optional.

```js
function withoutSpace(x) {
    // ...
}

function withSpace (x) {
    // ...
}
```

Some style guides may require a consistent spacing for function names.

## Rule Details

This rule aims to enforce a consistent spacing after function names. It takes one argument. If it is `"always"` then all function names must be followed by at least one space. If `"never"` then there should be no spaces between the name and the parameter list. The default is `"never"`.


The following patterns are considered problems:

```js
function foo (x) {
    // ...
}

var x = function named (x) {};

// When [1, "always"]
function bar(x) {
    // ...
}
```

The following patterns are not considered problems:

```js
function foo(x) {
    // ...
}

var x = function named(x) {};

// When [1, "always"]
function bar (x) {
    // ...
}
```

## Version

This rule was introduced in ESLint 0.11.0 and removed in 1.0.0-rc-1.

## Resources

* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/space-after-function-name.md)
