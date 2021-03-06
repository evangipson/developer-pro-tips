## JavaScript tips
- [Function Declarations](#function-declarations)
- [Function Expressions](#function-expressions)
- [Immediately Invoked Function Expressions](#immediately-invoked-function-expressions)
- [Class Declarations](#class-declarations)
- [Class Expressions](#class-expressions)
- [Named Class Expressions](#named-class-expressions)
- [For Loops](#for-loops)
- [Function Scope](#function-scope)
- [Softly Typed](#softly-typed)
- [Module Patterns](#module-patterns)
- [Terminology](#terminology)

### Function Declarations
***Function Declarations*** are **hoisted** to the top of the program by the JavaScript interpereter. They are intended to mimic the Java style of development.
```javascript
// Example Function Declaration:

function foo() { /* function contents */ }
```
### Function Expressions
***Function Expressions*** are **not hoisted**, but they are represented as variables or even anonymous functions, and therefore are more flexible than Function Declarations.
```javascript
// Example Function Expression (note the semi-colon... it *is* a variable after all):

var foo = function() { /* function contents */ };
```
### Immediately Invoked Function Expressions
***IIFE***s are **function expressions** which are **immediately invoked**. IFFEs are **not hoisted**. IIFEs are denoted with parenthesis wrapping each side of the IIFE, as well as empty parenthesis at the end of the IIFE (denoting the function should be executed immediately after it's created).
```javascript
// Example Immediately Invoked Function Expressions

(function() { /* function contents */ })(); // function will immediately execute
```
### Class Declarations
***Class Declarations*** are **not hoisted**, so you need to declare your class before you attempt to instantiate it.
```javascript
// Example of incorrect Class Declaration:

var foo = new Foo(); // ReferenceError
class Foo {}
``` 
```javascript
// Example of correct Class Declaration:

class Foo {}
var foo = new Foo();
```
### Class Expressions
***Class Expressions*** are also **not hoisted**. There are both Named Class Expressions and Unnamed Class Expressions. An Unnamed Class Expression will act as an anonymous Object, so if you want clarity or readability, using Named Class Expressions is a good idea.
```javascript
// Example of Unnamed Class Expression:

var Foo = class {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
};
```
### Named Class Expressions
The name of the class in the ***Named Class Expression*** is scoped to the class's body.
```javascript
// Example of Named Class Expression:

var Foo = class Bar {
  static greetingPrefix() {
    return 'Hello';
  }
  greeting() {
    return Bar.greeting();
  }
};
// Instantiate our class after we express it
// because class expressions aren't hoisted.
const foo = new Foo();
console.log(Foo.greeting()); // returns "Hello"
console.log(Bar); // throws "Uncaught ReferenceError: Bar is not defined"
```
### For Loops
For loops will run code a defined amount of times. There are a multiple kinds of for loops, here we will discuss **for** and **for...in** loops. You can use the syntax ```for(var i = 0; i < condition; i++)```. This will run the code ```condition``` times. **For...in** is used for objects generally, and ignores the inherited non-enumerable prototype properties of the object (such as ```Object```'s ```toString()``` method). It *does* include other inherited prototype properties such as ones the developer creates. For...in loops have the syntax ```for(var key in object)```. Generally you should be using for loops if you can.
```javascript
// Example of for loop:

for(var i = 0; i < 5; i++) {
  console.log(i); // Prints 0 - 4
}

// Example of for...in loop:

for(var key in object) {
  console.log(key, object.key);
}
```
### Function Scope
Variables have ***function scope***
```javascript
// Example of function scope:

console.log("variable i: " + i); // Prints "variable i: undefined"

var i = 0;
console.log("variable i: " + i); // Prints "variable i: 0"

function runThrough() {
  for(var i = 1; i <= 10; i++) {
    console.log("variable i: " + i); // Prints "variable i: 1-10"
  }
  console.log("variable i: " + i); // Prints "variable i: 11"
}

runThrough(); // Prints all the console.logs defined in runThrough()
console.log("variable i: " + i); // Prints "variable i: 0"
```
### Softly Typed
Variables are ***softly typed***
```javascript
// Example of softly typed variables:

function logI() {
  console.log("type of i is " + typeof(i) + ", value: " + i);
}

function startAsArray() {
  i = [];
  logI(); // prints "type of i is object, value: "

  i += 1;
  logI(); // prints "type of i is string, value: 1"

  i += "1";
  logI(); // prints "type of i is string, value: 11"

  i -= 1;
  logI(); // prints "type of i is number, value: 10"
}

function startAsObject() {
  i = {};
  logI(); // prints "type of i is object, value: [object Object]"

  i += 1;
  logI(); // prints "type of i is string, value: [object Object]1"

  i += "1";
  logI(); // prints "type of i is string, value: [object Object]11"

  i -= 1;
  logI(); // prints "type of i is number, value: NaN"
}

function startAsIncrement() {
  i += 1;
  logI(); // prints "type of i is number, value: NaN"

  i += "1";
  logI(); // prints "type of i is string, value: NaN1"

  i -= 1;
  logI(); // prints "type of i is number, value: NaN"
}

startAsArray();
startAsObject();
startAsIncrement();
```
### Module Patterns
#### Augmentation
```javascript
// File B, or the file that depends on File A to load.

/* The gist here is that File A creates the "FOO" variable,
 * and the declaration in File B takes in a parameter (fooModule)
 * so you'll have everything you need from File A in fooModule already,
 * and then harmlessly add functionality in File B before returning it
 * for use in File B anywhere below Foo's instantiation. */

var FOO = (function(fooModule) {
  // Augmentation
  fooModule.augmentedGreeting = function() {
    return fooModule.greeting + " World!";
  }
  // If we want external code to call the
  // augmentedGreeting function expression
  // above, we need to give back the internal
  // module we augmented.
  return fooModule;
}(FOO)); // Augmented Function Expression

FOO.augmentedGreeting(); // returns "Hello World!"
```
#### Loose Augmentation
- If you'd like to break your javascript into multiple files, you're going to have utilize a ***module pattern***, with some **loose augmentation**.
```javascript
// File A, or the file that needs to load first.

/* FOO isn't created yet, and that's what the "FOO || {}" is
 * doing in the Loosely Augmented Function Expression below.
 * The logic is "if we don't already have a FOO defined, let's make
 * one, otherwise, we can just augment the existing FOO (fooModule)
 * before we return it. */

var FOO = (function(fooModule) {
  // Initial data
  fooModule.greeting = "Hello";
  // Ensure our other file has access
  // the .greeting we set up above by returning
  // the module before FOO has finished executing.
  return fooModule;
}}(FOO || {})); // Loosely Augmented Function Expression
```
#### Exports and Imports
*Note: This feature is not implemented in any browsers natively at this time. It is implemented in many transpilers, such as [Babel](https://babeljs.io/) and [Webpack](https://webpack.github.io/).*
- **Exports** are great for when you need to break things across files! There are two ways **```export```** can be used.
  - ```export default``` is good when there is only 1 thing to be exported by the file. It allows for easy importing!
    - ```export default function() { // stuff }``` will yield ```import Foo from "./first-file";``` and then ```typeof Foo === "function"; // true!```.
  - **named ```export```s** allow you to export multiple things per file, and can be imported one of two ways.
    - ```export const Foo = 15;``` will allow you to write ```import {Foo} from "./first-file";``` and then ```Foo = 15; // true```.
    - ```export const Foo function(){ // stuff };``` will allow you to write ```import {Foo} from "./first-file";``` and then ```typeof Foo === "function"; // true!```.
- ```import``` is a little more straightforward:
  - ```import Foo from "./package"``` will **import** the **default export** in the **local** *"./package"*.
  - ```import Foo from "package"``` will **import** the **default export** in the **global** *"package"*.
  - ```import * as Foo from "package"``` will **import** any **export** in the global *"package"*.
  - ```import {Foo} from "package"``` will **import** an **export named "Foo"** in the global *"package"*.

## Terminology
**Hoisted:** Function declarations and function variables are always moved (‘hoisted’) to the top of their JavaScript scope by the JavaScript interpreter.

**Softly Typed:** JavaScript will do it's best to match the type for you, instead of you defining the type of variable (this is why "var" is used for all variables, instead of "string", "int", "bool", etc.).

**Function Scope:** Local variables exist only within the function body of which they are defined and will have a different scope for every call of that function. Global variables (variables not declared within a function scope) will be accessible during all of runtime.

**Module Pattern:** Using a single object between files and (loosely) augmenting it, then returning it before the augmentations end.
