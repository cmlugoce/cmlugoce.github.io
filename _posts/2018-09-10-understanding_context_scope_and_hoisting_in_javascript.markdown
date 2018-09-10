---
layout: post
title:      "Understanding Context, Scope, and Hoisting in Javascript"
date:       2018-09-10 20:58:57 +0000
permalink:  understanding_context_scope_and_hoisting_in_javascript
---


**Context vs Scope (the short answer)**

Scope pertains to the visibility of variables, and context refers to the object to which a function belongs.


**Context in Javascript**

Context is related to objects. It refers to the object to which a function belongs. When you use the JavaScript `this` keyword, it refers to the object to which function belongs.
```
var obj = {
    foo: function() {
        return this;   
    }
};

obj.foo() === obj; // true
```
For functions, the value of `this` is determined on how the function is called. When a function is called as a method of an object, the context is set to the object the method is called on. When creating an instance of an object with the new operator, `this` is set to the newly created instance. Outside of any function `this` refers to the global context (window object).

**Scope in Javascript**

Scope can be defined as the concept of *where something is available*. In Javascript it involves where declared variables and methods are available within our code. 

Variables defined inside a function are in local scope while variables defined outside of a function are in the global scope. Each function when invoked creates a new scope.

**Global Scope**

Any time that  you open up a document and begin writing code in JavaScript, you are in the global scope. A variable is in the Global scope if it's defined outside of a function. These variables can be access in any other scope.
```
var name = 'Cristina';
console.log(name);

function logName () {
    console.log(name);
}
logName();  //Cristina


```


**Local Scope**

Whenever we create a new scope within the global scope, we are creating a local scope. Locally scoped variables are only accessible where they are defined. The easiest way to create a new local scope is by simply creating a new function! Every function created in JavaScript creates a new local scope. Within a function, any variable created is locally scoped and can only be accessed within the function that they are defined. Local variables are deleted when the function completes.

Let's check the following example:

```
function example(){
  // *LOCAL*
  var wine = 'Malbec';
}
```

We created a function and declared the variable `wine` in it. Let's throw a global variable and see what happens:
```
var beer = 'Stout';
console.log(beer); // Stout
function example(){
  var wine = 'Malbec';
  console.log(beer); // Stout
}
console.log(beer); // Stout
```
Since the variable `beer` was created in the global scope it can be accesed anywhere. If we try to do same thing with the variable `wine` we will get an error:
```
var beer = 'Stout';
console.log(wine); // Uncaught ReferenceError: wine is not defined
function example(){
  var wine = 'Malbec';
  console.log(wine); 
}
example(); //Malbec
console.log(wine); // Uncaught ReferenceError: wine is not defined
```

**Block Scope**

 As of ES6, JavaScript has partial support for block scoping. Two more keywords: `let` and `const` were added, and they can be used to declare variables.  The `var` variable is not block scoped, so it can't be used forblock scopes like if, for, while, {}, etc. On the other hand,  `let` and `const` are block scoped!
 Let's look at an example:
 
 ```
if (true) {
  var myVar = 100;
}
 
myVar; //100
 ```
 
 In this case, the variable is accessed out of the block, and has a local scope (not block-scoped)!!
 Let's try with the `let` keyword:
 
 ```
 if (true) {
  let myVar = 100;
}
 
myVar; //Uncaught ReferenceError: myVar is not defined
 ```
 Declaring with `let` or `const`, the variables can't be accessed outside of the block-scope.
 
 **Hoisting**
 
 In Javascript, the term *hoisting* is used to describe a behaviour of the Javascript interpreter. The interpreter moves the function and variable declarations to the top of the current scope. Basically, it means that  a variable can be used before it has been declared.
 
 ```
(function() {  
   thecoffee();  //dark
   return;
   function thecoffee() {
       console.log("dark");
   }
})();

```

In ES6, variables declared using `let` or `const` are hoisted like those declared using `var` are , the difference is that variables declared using `var` are automatically initialized to a value of undefined and the variables declared using `let` or `const` are not. Because of this, is more practical to say that variables with `let` and `const` are not hoisted.

 **Best Hoisting practices**
  1. Declare all your functions at the top of their scope!!
  2. Only use `let` and `const`


