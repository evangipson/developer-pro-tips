## What *is* Ecmascript 6?
EcmaScript 6, also known as ECMAScript 2015, is a standard created for JavaScript. EcmaScript aims to be an improvement to the rigidity, reliability, and formality of JavaScript. You can see a great concise [list of all the features here](http://es6-features.org/).

## How do I use it?
It's easy! In any [supported browser](http://kangax.github.io/compat-table/es6/), use the following line:
```javascript
'use strict;'
```
It's as easy as that!

## What's new?
- [Block Scope](#block-scope)
  - [Using let, const, and var](#using-let-const-and-var)
- [Default Parameters](#default-parameters)
- [Rest Parameters](#rest-parameters)
- [Spread Syntax](#spread-syntax)

## Block Scope
Variables can now have their scope limited to the block of code they are in, instead of the function. To make your variable block scope, use `let` or `const`.

### Using `let`, `const`, and `var`
If you want a block-scoped variable, and you want to be able to change ("mutate") it, use `let`.

If you want a block-scoped variable, and you want it to stay the same ("immutable"), use `const`.

If you want a function-scoped variable, use `var`, unless you don't want the variable to change... then consider using `const` at a higher level.

## Default Parameters
Parameters can have their values set in the function declaration, and then they are optional when the function is called. If they are passed when the function is invoked, the value passed in overwrites the default value.
```javascript
// Example of Default Parameters

f(x, y = 1, z = 10) {
 return x + y + z;
}
f(1, 2); // returns 13
f(10); // returns 21
f(10, 10, 10); // returns 30
f(10, 2, 1); // returns 13
f(100, 0); // returns 110
```

## Rest Parameters
The *rest parameter* syntax represents an undetermined number of arguments as an array.
```javascript
// Example of Rest Parameters

f(x, y, ...z) {
  return x + y + z.length;
}
f(1, 1); // returns 2
f(1, 1, 1); // returns 3
f(1, 1, 1, 2, 3, 4); // returns 6
f(1, 1, [1, 1], [1, 1]); // returns 4
```

## Spread Syntax
*Spread syntax* is a tool to expand expressions where multiple arguments, variables, or elements are expected.
```javascript
// Example of Spread Syntax

// For function calls
f(...iterableObj);
// For array literals
[...iterableObj, 4, 5, 6];

// Copy an array using spread syntax
var arr = [1,2,3];
var arr2 = [...arr];
arr2.push(4); 

// arr2 becomes [1,2,3,4]
// arr remains unaffected
```
