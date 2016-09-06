## JavaScript tips
- Function Declarations are **hoisted** to the top of the program by the JavaScript interpereter. They are intended to mimic the Java style of development.
  - Example Function Declaration:
```
function foo() { //function contents }
```
- Function Expressions are not hoisted, but they are represented as variables or even anonymous functions, and therefore are more flexible than Function Declarations.
  - Example Function Expression (note the semi-colon, it *is* a variable after all):
```
var foo = function() { //function contents };
```
- Variables have **function scope**
- Variables are **softly typed**

## Terminology
**Hoisted:** Function declarations and function variables are always moved (‘hoisted’) to the top of their JavaScript scope by the JavaScript interpreter.

**Softly Typed:** JavaScript will do it's best to match the type for you, instead of you defining the type of variable (this is why "var" is used for all variables, instead of "string", "int", "bool", etc.).

**Function Scope:** Local variables exist only within the function body of which they are defined and will have a different scope for every call of that function. Global variables (variables not declared within a function scope) will be accessible during all of runtime.
