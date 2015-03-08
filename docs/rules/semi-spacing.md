---
title: ESLint
layout: doc
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->
# Enforce spacing before and after semicolons (semi-spacing)

JavaScript allows you to place unnecessary spaces before or after a semicolon.

Disallowing or enforcing space around a semicolon can improve the readability of your program.

```js
var a = "b" ;

var c = "d";var e = "f";
```

## Rule Details

This rule aims to enforce spacing around a semicolon. This rule prevents the use of spaces before a semicolon in expressions.

### Options

The rule takes one option, an object, which has two keys `before` and `after` having boolean values `true` or `false`.
If `before` is `true`, space is enforced before semicolons and if it's `false`, space is disallowed before semicolons.
If `after` is `true`, space is enforced after semicolons and if it's `false`, space is disallowed after semicolons.
The `after` option will be only applied if a semicolon is not at the end of line.

The default is `{"before": false, "after": true}`.

```json
    "semi-spacing": [2, {"before": false, "after": true}]
```

#### {"before": false, "after": true}

This is the default option. It enforces spacing after semicolons and disallows spacing before semicolons.

The following patterns are considered warnings:

```js
var foo ;
var foo;var bar;
throw new Error("error") ;
while (a) { break ; }
for (i = 0 ; i < 10 ; i++) {}
for (i = 0;i < 10;i++) {}
```

The following patterns are not warnings:

```js
var foo;
var foo; var bar;
throw new Error("error");
while (a) { break; }
for (i = 0; i < 10; i++) {}
```

#### {"before": true, "after": false}

This option enforces spacing before semicolons and disallows spacing after semicolons.

The following patterns are considered warnings:

```js
var foo;
var foo ; var bar;
throw new Error("error");
while (a) { break; }
for (i = 0;i < 10;i++) {}
for (i = 0; i < 10; i++) {}
```

The following patterns are not warnings:

```js
var foo ;
var foo ;var bar;
throw new Error("error") ;
while (a) {break ;}
for (i = 0 ;i < 10 ;i++) {}
```

## When Not To Use It

You can turn this rule off if you are not concerned with the consistency of spacing before or after semicolons.

## Related Rules

* [semi](semi.html)
* [no-extra-semi](no-extra-semi.html)
* [comma-spacing](comma-spacing.html)

## Version

This rule was introduced in ESLint 0.16.0.

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/semi-spacing.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/semi-spacing.md)