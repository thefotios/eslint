# Treat var as Block Scoped (block-scoped-var)

The `block-scoped-var` rule generates warnings when variables are used outside of the block in which they were defined. This emulates C-style block scope.

```js
function doSomething() {
    if (true) {
        var build = true;
    }

    console.log(build);
}
```

## Rule Details

This rule aims to reduce the usage of variables outside of their binding context and emulate traditional block scope from other languages. This is to help newcomers to the language avoid difficult bugs with variable hoisting.

### Options

This rule has no options other than the severity (`0`, `1`, or `2`).

#### Usage

You can set the rule configuration like this:

```json
"block-scoped-var": 2
```


The following patterns are considered warnings:

```js
/*eslint block-scoped-var: 1*/

function doSomething() {
    if (true) {
        var build = true;
    }

    console.log(build);
}
```

```js
/*eslint block-scoped-var: 1*/

function doAnother() {
    try {
        var build = 1;
    } catch (e) {
        var f = build;
    }
}
```

The following patterns are not warnings:

```js
/*eslint block-scoped-var: 2*/

function doSomething() {
    var build;

    if (true) {
        build = true;
    }

    console.log(build);
}
```

## Further Reading

* [JavaScript Scoping and Hoisting](http://www.adequatelygood.com/JavaScript-Scoping-and-Hoisting.html)
* [var Hoisting](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var#var_hoisting)
