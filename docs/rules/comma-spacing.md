# Enforces spacing around commas (comma-spacing)

Spacing around commas improve readability of a list of items. Although most of the style guidelines for languages prescribe adding a space after a comma and not before it, it is subjective to the preferences of a project.

```js
var foo = 1, bar = 2;
var foo = 1 ,bar = 2;
```

## Rule Details

This rule aims to enforce spacing around a comma. As such, it warns whenever it sees a missing or unwanted space in commas of variable declaration, object property, function parameter, sequence and array element.

### Options

The rule takes one option, an object, which has two keys `before` and `after` having boolean values `true` or `false`.

* `"before": true` enforces at least one space before commas
* `"before": false` disallows any spaces before commas (Default)
* `"after": true` enforces at least one space after commas (Default)
* `"after": false` disallows any spaces after commas

#### Usage

You can set the rule configuration like this:

```json
    "comma-spacing": [2, {"before": false, "after": true}]
```

The following examples show two primary usages of this option.

#### {"before": false, "after": true}

This is the default option. It enforces spacing after commas and disallows spacing before commas.

The following patterns are considered warnings:

```js
/*eslint comma-spacing: [1, {"before": false, "after": true}]*/

var foo = 1 ,bar = 2;
var arr = [1 , 2];
var obj = {"foo": "bar" ,"baz": "qur"};
foo(a ,b);
new Foo(a ,b);
function foo(a ,b){}
a ,b
```

The following patterns are not warnings:

```js
/*eslint comma-spacing: [2, {"before": false, "after": true}]*/

var foo = 1, bar = 2
    , baz = 3;
var arr = [1, 2];
var obj = {"foo": "bar", "baz": "qur"};
foo(a, b);
new Foo(a, b);
function foo(a, b){}
a, b
```

#### {"before": true, "after": false}

This option enforces spacing before commas and disallows spacing after commas.

The following patterns are considered warnings:

```js
/*eslint comma-spacing: [1, {"before": true, "after": false}]*/

var foo = 1, bar = 2;
var arr = [1 , 2];
var obj = {"foo": "bar", "baz": "qur"};
new Foo(a,b);
function foo(a,b){}
a, b
```

The following patterns are not warnings:

```js
/*eslint comma-spacing: [2, {"before": true, "after": false}]*/

var foo = 1 ,bar = 2 ,
    baz = true;
var arr = [1 ,2];
var obj = {"foo": "bar" ,"baz": "qur"};
foo(a ,b);
new Foo(a ,b);
function foo(a ,b){}
a ,b
```

## When Not To Use It

Do not use this rule if your project will not be following a consistent comma-spacing pattern.


## Further Reading

* [Javascript](http://javascript.crockford.com/code.html)
* [Dojo Style Guide](http://dojotoolkit.org/community/styleGuide)


## Related Rules

* [comma-style](comma-style.md)
* [space-in-brackets](space-in-brackets.md) (deprecated)
* [space-in-parens](space-in-parens.md)
* [space-infix-ops](space-infix-ops.md)
* [space-after-keywords](space-after-keywords)
* [space-unary-ops](space-unary-ops)
* [space-return-throw-case](space-return-throw-case)
