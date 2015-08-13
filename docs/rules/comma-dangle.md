# Disallow or Enforce Dangling Commas (comma-dangle)

Trailing commas in object literals are valid according to the ECMAScript 5 (and ECMAScript 3!) spec. However, IE8 (when not in IE8 document mode) and below will throw an error when it encounters trailing commas in JavaScript.

```js
var foo = {
    bar: "baz",
    qux: "quux",
};
```

On the other hand, trailing commas simplify adding and removing items to objects and arrays, since only the lines you are modifying must be touched.

## Rule Details

This rule enforces consistent use of trailing commas in object and array literals.

### Options

This rule takes one string argument:

* `"never"` warns whenever a trailing comma is detected (Default)
* `"always"` warns whenever a missing comma is detected
* `"always-multiline"` warns if there is a missing trailing comma on arrays or objects that span multiple lines, and warns if there is a trailing comma present on single line arrays or objects.


#### never

The following patterns are considered warnings when configured `"never"`:

```js
/*eslint comma-dangle: [1, "never"]*/

var foo = {
    bar: "baz",
    qux: "quux",
};

var arr = [1,2,];

foo({
  bar: "baz",
  qux: "quux",
});
```

The following patterns are not considered warnings when configured `"never"`:

```js
/*eslint comma-dangle: [2, "never"]*/

var foo = {
    bar: "baz",
    qux: "quux"
};

var arr = [1,2];

foo({
  bar: "baz",
  qux: "quux"
});
```

#### always

The following patterns are considered warnings when configured `"always"`:

```js
/*eslint comma-dangle: [1, "always"]*/

var foo = {
    bar: "baz",
    qux: "quux"
};

var arr = [1,2];

foo({
  bar: "baz",
  qux: "quux"
});
```

The following patterns are not considered warnings when configured `"always"`:

```js
/*eslint comma-dangle: [2, "always"]*/

var foo = {
    bar: "baz",
    qux: "quux",
};

var arr = [1,2,];

foo({
  bar: "baz",
  qux: "quux",
});
```

#### always-multiline

The following patterns are considered warnings when configured `"always-multiline"`:

```js
/*eslint comma-dangle: [1, "always-multiline"]*/

var foo = {
    bar: "baz",
    qux: "quux"
};

var foo = { bar: "baz", qux: "quux", };

var arr = [1,2,];

var arr = [1,
    2,];

var arr = [
    1,
    2
];

foo({
  bar: "baz",
  qux: "quux"
});
```

The following patterns are not considered warnings when configured `"always-multiline"`:

```js
/*eslint comma-dangle: [2, "always-multiline"]*/

var foo = {
    bar: "baz",
    qux: "quux",
};

var foo = {bar: "baz", qux: "quux"};
var arr = [1,2];

var arr = [1,
    2];

var arr = [
    1,
    2,
];

foo({
  bar: "baz",
  qux: "quux",
});
```

## When Not To Use It

You can leave this rule off if you are not concerned with dangling commas.
