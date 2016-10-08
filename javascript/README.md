## JavaScript tips
- Function Declarations are **hoisted** to the top of the program by the JavaScript interpereter. They are intended to mimic the Java style of development.
```javascript
// Example Function Declaration:

function foo() { /* function contents */ }
```
- Function Expressions are **not hoisted**, but they are represented as variables or even anonymous functions, and therefore are more flexible than Function Declarations.
```javascript
// Example Function Expression (note the semi-colon... it *is* a variable after all):

var foo = function() { /* function contents */ };
```
- Class Declarations are **not hoisted**, so you need to declare your class before you attempt to instantiate it.
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
- Class Expressions are also **not hoisted**. There are both Named Class Expressions and Unnamed Class Expressions. An Unnamed Class Expression will act as an anonymous Object, so if you want clarity or readability, using Named Class Expressions is a good idea
```javascript
// Example of Unnamed Class Expression:

var Foo = class {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
};
```
- The name of the class in the Named Class expression is scoped to the class's body.
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
- Variables have **function scope**
- Variables are **softly typed**
- If you'd like to break your javascript into multiple files, you're going to have utilize a **module pattern**, with some *loose augmentation*.
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

## Terminology
**Hoisted:** Function declarations and function variables are always moved (‘hoisted’) to the top of their JavaScript scope by the JavaScript interpreter.

**Softly Typed:** JavaScript will do it's best to match the type for you, instead of you defining the type of variable (this is why "var" is used for all variables, instead of "string", "int", "bool", etc.).

**Function Scope:** Local variables exist only within the function body of which they are defined and will have a different scope for every call of that function. Global variables (variables not declared within a function scope) will be accessible during all of runtime.

**Module Pattern:** Using a single object between files and (loosely) augmenting it, then returning it before the augmentations end.
