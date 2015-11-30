---
title: Rule max-depth
layout: doc
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->
# Limit Maximum Depth (max-depth)

The `max-depth` rule allows you to specify the maximum depth blocks can be nested.

```js
function foo() {
  for (;;) { // Nested 1 deep.
    if (true) { // Nested 2 deep.
      if (true) { // Nested 3 deep.

      }
    }
  }
}
```

## Rule Details

This rule aims to reduce the complexity of your code by allowing you to configure the maximum depth blocks can be nested in a function. As such, it will warn when blocks are nested too deeply.

### Options

The default depth above which this rule will warn is `4`.  You can configure the depth as an option by using the second argument in your configuration. For example, this sets the rule as an error with a maximum depth of 10:

```json
"max-depth": [2, 10]
```

The following patterns are considered problems:

```js
/*eslint max-depth: [2, 2]*/

function foo() {
  for (;;) {
    if (true) {
      if (true) { /*error Blocks are nested too deeply (3).*/

      }
    }
  }
}
```

The following patterns are not considered problems:

```js
/*eslint max-depth: [2, 2]*/

function foo() {
  for (;;) {
    if (true) {

    }
  }
}
```


## Related Rules

* [complexity](complexity)
* [max-len](max-len)
* [max-nested-callbacks](max-nested-callbacks)
* [max-params](max-params)
* [max-statements](max-statements)

## Version

This rule was introduced in ESLint 0.0.9.

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/max-depth.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/max-depth.md)
