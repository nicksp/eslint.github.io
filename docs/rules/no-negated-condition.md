---
title: Rule no-negated-condition
layout: doc
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->

# Disallow use of negated expressions in conditions (no-negated-condition)

Checks against the use of a negated expression in an if condition when the else branch is not empty or in a ternary operator. Negated conditions are more difficult to understand. Code can be made more readable by inverting the condition instead.

For example:

```js
if (!a) {
    doSomething();
}
else {
    doSomethingElse();
}
```

should instead be written as:

```js
if (a) {
    doSomethingElse();
}
else {
    doSomething();
}
```

## Rule Details

The rule is aimed at preventing the use of a negated expression in a condition.

The following patterns are considered warnings:

```js
/*eslint no-negated-condition: "error"*/

if (!a) {
    doSomething();
} else {
    doSomethingElse();
}

if (a != b) {
    doSomething();
} else {
    doSomethingElse();
}

if (a !== b) {
    doSomething();
} else {
    doSomethingElse();
}


!a ? b : c

```

The following patterns are not warnings:


```js
/*eslint no-negated-condition: "error"*/

if (!a) {
    doSomething();
}

if (!a) {
    doSomething();
} else if (b) {
    doSomething();
}

if (a != b) {
    doSomething();
}

a ? b : c

```

## Version

This rule was introduced in ESLint 1.6.0.

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/no-negated-condition.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/no-negated-condition.md)
