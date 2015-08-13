# Require space before/after arrow function's arrow (arrow-spacing)

This rule aims to normalize the style of spacing before/after an arrow function's arrow(`=>`).

```js
// With spaces before and after
(a) => {}

// No spaces before or after
(a)=>{}
```

## Rule Details

### Options

This rule takes an object argument with `"before"` and `"after"` properties, each with a Boolean value.

* `"before": true` enforces at least one space before the arrow (Default)
* `"before": false` prohibits spaces before the arrow
* `"after": true` enforces at least one space after the arrow (Default)
* `"after": false` prohibits spaces after the arrow

In short, `true` means there should be **one or more spaces** and `false` means **no spaces**.

#### Usage

You can set the rule configuration like this:

```json
"arrow-spacing": [2, { "before": false }]
```

#### before and after both true

The following patterns are considered warnings if `{ "before": true, "after": true }`, which is the default case.

```js
/*eslint arrow-spacing: 1*/

()=> {};
() =>{};
(a)=> {};
(a) =>{};
a =>a;
a=> a;
()=> {'\n'};
() =>{'\n'};
```

The following patterns are not warnings if `{ "before": true, "after": true }`.

```js
/*eslint arrow-spacing: 2*/

() => {};
(a) => {};
a => a;
() => {'\n'};
```

#### before and after both false

The following patterns are not warnings if `{ "before": false, "after": false }`.

```js
/*eslint arrow-spacing: [2, { "before": false, "after": false }]*/

()=>{};
(a)=>{};
a=>a;
()=>{'\n'};
```

#### before true, after false

The following patterns are not warnings if `{ "before": true, "after": false }`.

```js
/*eslint arrow-spacing: [2, { "before": true, "after": false }]*/

() =>{};
(a) =>{};
a =>a;
() =>{'\n'};
```

#### before false, after true

The following patterns are not warnings if `{ "before": false, "after": true }`.

```js
/*eslint arrow-spacing: [2, { "before": false, "after": true }]*/

()=> {};
(a)=> {};
a=> a;
()=> {'\n'};
```
