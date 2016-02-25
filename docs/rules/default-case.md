---
title: Rule default-case
layout: doc
translator: fengnana
proofreader: sunshiner
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->
# Require Default Case in Switch Statements (default-case)
# 要求switch语句中有default分支 (default-case)

Some code conventions require that all `switch` statements have a `default` case, even if the default case is empty, such as:

一些编码规范中，要求所有的`switch` 语句中必须包含`default`分支，即使default分支中没有任何代码，如下所示：

```js
switch (foo) {
    case 1:
        doSomething();
        break;

    case 2:
        doSomething();
        break;

    default:
        // do nothing
}
```

The thinking is that it's better to always explicitly state what the default behavior should be so that it's clear whether or not the developer forgot to include the default behavior by mistake.

考虑到开发人员可能会忘记定义默认分支而导致程序发生错误，所以明确规定定义默认分支是很好的选择。

Other code conventions allow you to skip the `default` case so long as there is a comment indicating the omission is intentional, such as:

有些代码规范中允许省略掉`default`分支，但是要写明注释以说明是故意为之。如下：

```js
switch (foo) {
    case 1:
        doSomething();
        break;

    case 2:
        doSomething();
        break;

    // no default
}
```

Once again, the intent here is to show that the developer intended for there to be no default behavior.

再次指出，以上示例的前提是开发者并没有默认分支的情况需要处理。

## Rule Details

This rule aims to require `default` case in `switch` statements. You may optionally include a `// no default` after the last `case` if there is no `default` case.

此规则的目的是在`switch`语句中强制声明`default`分支。或者也可以在最后一个`case`分支下，使用`// no default`来表明此处不需要`default`分支。

The following pattern is considered a warning:

错误示例如下：

```js
/*eslint default-case: 2*/

switch (a) {       /*error Expected a default case.*/
    case 1:
        /* code */
        break;
}

```

The following patterns are not considered problems:

以下模式被认为是没有问题的：

```js
/*eslint default-case: 2*/

switch (a) {
    case 1:
        /* code */
        break;

    default:
        /* code */
        break;
}


switch (a) {
    case 1:
        /* code */
        break;

    // no default
}

```


## When Not To Use It

If you don't want to enforce a `default` case for `switch` statements, you can safely disable this rule.

如果不想要求`switch`中必须要有`default`分支，禁用此规则即可。

## Related Rules

* [no-fallthrough](no-fallthrough)

## Version

This rule was introduced in ESLint 0.6.0.

该规则在ESLint 0.6.0 中被引入。

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/default-case.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/default-case.md)
