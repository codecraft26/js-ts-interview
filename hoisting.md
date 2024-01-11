## Hoisting 

Hoisting in JavaScript is a behavior where variable and function declarations are moved to the top of their containing scope during the compilation phase, before the code has been executed. This can lead to behaviors where variables and functions can be used before they appear to be declared in the code. However, it's important to understand the nuances of how hoisting works for different types of declarations.

- Varibale Hoisting:-With var declarations, the variable is hoisted to the top of its containing scope (either the function or global scope). The variable is initialized with undefined, which allows you to access the variable before its actual declaration, but its value will be undefined until you assign a value to it.
let and const variables are also hoisted to the top of their block scope, but they are not initialized. Attempting to access them before the declaration results in a ReferenceError. This period from the start of the block until the declaration is known as the Temporal Dead Zone (TDZ).

- Function Hoisting:- Function declarations are hoisted to the top of their containing scope, and the entire function body is also hoisted. This means you can call a function before it appears to be defined in the code.
Function expressions are treated differently depending on how they are declared. If a function expression is assigned to a var variable, the variable name is hoisted but not the function assignment. If it is assigned to a let or const variable, it will be in the TDZ and accessing it before the declaration will result in an error.


### Example of Hoisting

```javascript
console.log(myVar); // undefined
var myVar = 'Hello';
```

### Function Hoisting

```javascript
myFunction(); // This works and logs "Hello World"
function myFunction() {
  console.log("Hello World");
}
```

### Function Expression (not hoisted)

```javascript
myFuncExpr(); // TypeError: myFuncExpr is not a function
var myFuncExpr = function() {
  console.log("Hello");
};
```
### let and const (Temporal Dead Zone)

```javascript
console.log(myLet); // ReferenceError: Cannot access 'myLet' before initialization
let myLet = 'Hello';

console.log(myConst); // ReferenceError: Cannot access 'myConst' before initialization
const myConst = 'World';
```


Understanding hoisting is crucial in JavaScript as it explains why variables and functions can be used before they are declared and helps to avoid common mistakes like using a variable before it is initialized or understanding function behavior within different scopes.

###
