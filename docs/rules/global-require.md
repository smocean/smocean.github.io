---
title: Rule global-require
layout: doc
translator: ILFront-End
proofreader: sunshiner
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->

# Enforce require() on the top-level module scope. (global-require)

# 强制在顶部加载模块 (global-require)


In Node.js, module dependencies are included using the `require()` function, such as:

在Node.js中，引入模块依赖使用`require()`函数，例如：

```js
var fs = require("fs");
```

While `require()` may be called anywhere in code, some style guides prescribe that it should be called only in the top level of a module to make it easier to identify dependencies. For instance, it's arguably harder to identify dependencies when they are deeply nested inside of functions and other statements:

然而`require()`可以在代码的任何地方被调用，一些编码规范规定必须在模块的最外层作用域调用`require()`函数以便于于识别依赖。举个例子：下面的代码里在函数里面调用`require()`方法，这样就不便于识别依赖。

```js
function foo() {

    if (condition) {
        var fs = require("fs");
    }
}
```

Since `require()` does a synchronous load, it can cause performance problems when used in other locations.

因为`require()`是同步加载的，当在其他位置使用时会导致性能问题。

Further, ES6 modules mandate that `import` and `export` statements can only occur in the top level of the module's body.

此外，ES6模块要求`import` 和 `export` 语句只能放在模块顶部。

## Rule Details

This rule requires all calls to `require()` to be at the top level of the module, similar to ES6 `import` and `export` statements, which also can occur only at the top level.

此规则要求所有调用`require()`必须在模块范围顶部，与ES6中`import` 和 `export` 语句相同，也只能放在顶部。

You can enable this rule with the following syntax:

你能启动这个规则通过下面的语法：

```json
"global-require": 2
```

The following patterns are considered problems:

以下模式被认为有问题：

```js
/*eslint global-require: 2*/
/*eslint-env es6*/

// calling require() inside of a function is not allowed
function readFile(filename, callback) {
    var fs = require('fs');
    fs.readFile(filename, callback)
}

// conditional requires like this are also not allowed
if (DEBUG) { require('debug'); }

// a require() in a switch statement is also flagged
switch(x) { case '1': require('1'); break; }

// you may not require() inside an arrow function body
var getModule = (name) => require(name);

// you may not require() inside of a function body as well
function getModule(name) { return require(name); }

// you may not require() inside of a try/catch block
try {
    require(unsafeModule);
} catch(e) {
    console.log(e);
}
```

The following patterns are not considered problems:、

以下模式被认为没问题：

```js
/*eslint global-require: 2*/

// all these variations of require() are ok
require('x');
var y = require('y');
var z;
z = require('z').initialize();

// requiring a module and using it in a function is ok
var fs = require('fs');
function readFile(filename, callback) {
    fs.readFile(filename, callback)
}

// you can use a ternary to determine which module to require
var logger = DEBUG ? require('dev-logger') : require('logger');

// if you want you can require() at the end of your module
function doSomethingA() {}
function doSomethingB() {}
var x = require("x"),
    z = require("z");
```

## When Not To Use It

If you have a module that must be initialized with information that comes from the file-system or if a module is only used in very rare situations and will cause significant overhead to load it may make sense to disable the rule. If you need to `require()` an optional dependency inside of a `try`/`catch`, you can disable this rule for just that dependency using the `// eslint disable-line global-require` comment.

如果一个模块必须使用来至于系统文件的信息初始化或者一个模块仅仅在非常稀少的情况下使用，将导致重大开销去加载模块，禁用此规则将是有意义的。如果你需要在`try`/`catch`内部使用`require()`一个可选依赖，你可以使用`// eslint disable-line global-require`注释只对此依赖禁用此规则。

## Version

This rule was introduced in ESLint 1.4.0.

此规则在ESLint 1.4.0中被引入。

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/global-require.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/global-require.md)
