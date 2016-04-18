---
title: Rule prefer-arrow-callback
layout: doc
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->

# Suggest using arrow functions as callbacks. (prefer-arrow-callback)

Arrow functions are suited to callbacks, because:

- `this` keywords in arrow functions bind to the upper scope's.
- The notation of the arrow function is shorter than function expression's.

## Rule Details

This rule is aimed to flag usage of function expressions in an argument list.

The following patterns are considered problems:

```js
/*eslint prefer-arrow-callback: "error"*/

foo(function(a) { return a; });
foo(function() { return this.a; }.bind(this));
```

The following patterns are not considered problems:

```js
/*eslint prefer-arrow-callback: "error"*/
/*eslint-env es6*/

foo(a => a);
foo(function*() { yield; });

// this is not a callback.
var foo = function foo(a) { return a; };

// using `this` without `.bind(this)`.
foo(function() { return this.a; });

// recursively.
foo(function bar(n) { return n && n + bar(n - 1); });
```

## Options

This rule takes one optional argument, an object with a boolean property `"allowNamedFunctions"`. It is `false` by default. If it is set to `true`, this rule doesn't warn on named functions used as callbacks.

### allowNamedFunctions

Examples of **correct** code for the `{ "allowNamedFunctions": true }` option:

```js
/*eslint prefer-arrow-callback: ["error", { "allowNamedFunctions": true }]*/

foo(function bar() {});
```

## When Not To Use It

This rule should not be used in ES3/5 environments.

In ES2015 (ES6) or later, if you don't want to be notified about function expressions in an argument list, you can safely disable this rule.

## Version

This rule was introduced in ESLint 1.2.0.

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/prefer-arrow-callback.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/prefer-arrow-callback.md)