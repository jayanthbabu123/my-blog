+++
title = '7 Differences between arrow functions and regular functions in JavaScript'
date = 2023-12-09T23:44:12+05:30
tags = [
  "JavaScript",
  "ES6",
  "Arrow Functions",
  "Regular Functions",
  "Programming",
  "Web Development",
  "Function Syntax",
  "Coding Best Practices",
  "JavaScript Functions"
]
categories = ["JavaScript"]
image= "/images/arrow-regular.webp"
draft = false
+++

![How Real DOM works with HTML and JavaScript](/images/arrow-regular.webp)

### Introduction 🚀

Welcome to the world of JavaScript! In this article, we're diving into one of the key parts of JavaScript coding: functions. We'll compare two types of functions you'll often see — Regular Functions and Arrow Functions, which were added in the latest version, ES6. These functions make your code work, and understanding how they differ can really help you write better JavaScript.

Whether you’re just starting out or have been coding for a while, this guide will shed light on how these functions work and why they're important in today's coding world. So, let's get started and unlock the secrets of JavaScript functions!

**Types of Functions in JavaScript**

In JavaScript, a function is a block of code designed to perform a particular task. Functions allow programmers to break up a large program into smaller, more manageable components. This modular approach avoids the need for repetitive code, enhancing maintainability and readability.

There are two primary types of functions in JavaScript:

1. Regular Functions
2. Arrow Functions (Introduced in ES6)

**1. Regular Functions:**

Regular functions in JavaScript can be defined in two ways: `Function declaration` and `Function expression`. The main difference between these two approaches is how and when the functions are loaded and invoked.

**Function Declaration:** Function declarations are hoisted in JavaScript, which means they are raised to the top of their scope before code execution. In simpler terms, this allows you to call a function before you've written it in your script.

```javascript
console.log(add(2, 3)); // Works fine, outputs 5
function add(a, b) {
  return a + b;
}
```

This behavior happens because the `JavaScript interpreter` moves all function declarations to the top of their containing scope during the compile phase. This means that the function is available throughout their entire enclosing scope, regardless of where the function declaration actually occurs.

**Function Expression:** In contrast, function expressions are not hoisted. This means you must define the function before you attempt to use it in your code, otherwise, JavaScript will throw an error.

```javascript
console.log(sum(2, 3)); // Throws an error: sum is not a function
const sum = function (a, b) {
  return a + b;
};
```

**2. Arrow Functions**

The `arrow function` — also called the `fat arrow function` — is a new feature introduced in ES6 that is a more concise syntax for writing function expressions. It allows you to create functions more cleanly compared to regular functions. There is no declaration approach here, we can write by using Function expressions only.

```javascript
// Arrow Function Expression
const add = (a, b) => {
  return a + b;
};

// More simple and concise syntax
const add = (a, b) => a + b;
```

Key differences between regular and arrow functions are

1. Syntax
2. No arguments (arguments are array-like objects)
3. No prototype object for the Arrow function
4. Cannot be invoked with a new keyword (Not a constructor function)
5. No own this (call, apply & bind won't work as expected)
6. Duplicate-named parameters are not allowed
7. It cannot be used as a Generator function

**1. Syntax ☕**

`Arrow functions` provide a shorter and more concise syntax. This is particularly useful for single-expression functions, as it allows for a cleaner and more readable code style.

```javascript
// Regular Function
function square(x) {
  return x * x;
}
// Arrow Function
const square = (x) => x * x; // More concise
```

In this example, the arrow function simplifies the function definition, making the code more elegant and easier to understand at a glance.

**2. No 'arguments' Object 🌍**

One of the fundamental differences is the lack of the `arguments` object in arrow functions. In regular functions, `arguments` is an array-like object that allows you to work with a function’s `arguments`.

```javascript
function regularFunction() {
  console.log(arguments[0]); // Access first argument
}
regularFunction(1, 2, 3); // Outputs: 1
```

In contrast, arrow functions do not provide the arguments object. However, you can achieve similar functionality using `rest parameters`, which allow you to handle an indefinite number of arguments as an array.

```javascript
const arrowFunction = (...args) => {
  console.log(args[0]); // Access first argument
};
arrowFunction(1, 2, 3); // Outputs: 1
```

**3. No Prototype Property 📝**

Arrow functions do not have a `prototype` property. In JavaScript, the prototype is an object associated with every functions and objects by default. Regular functions have this property, but arrow functions do not, making them unsuitable for certain tasks like object constructor functions.

```javascript
const regularFn = function () {};
console.log(typeof regularFn.prototype); // 'object'

const arrowFn = () => {};
console.log(typeof arrowFn.prototype); // 'undefined'
```

**4. Cannot Be Invoked with New Keyword 🎈**

Arrow functions cannot be used as `constructors`. This means you cannot use the new keyword with arrow functions, as they do not have their own this context or a prototype property.

```javascript
const arrowFunction = () => {};
const instance = new arrowFunction(); // Throws an error
```

**5. No Own 'this' Binding (call, apply & bind won’t work as expected) 🎶**

One of the key differences between regular and arrow functions is how they handle the `this` keyword. In JavaScript, this refers to the context in which a function is executed. This context can change based on how the function is called, especially in the case of regular functions. However, arrow functions handle this differently.

**Regular Function 'this' Context:**
In a regular function, `this` is determined by how the function is called. It can vary and is not fixed at the time of function declaration.

```javascript
function myFunction() {
  console.log(this);
}

const myObject = {
  method: myFunction,
};

myFunction(); // 'this' will refer to the global object or undefined in strict mode
myObject.method(); // 'this' will refer to 'myObject'
```

In this example, the value of `this` inside myFunction changes depending on how it's called. When called as myFunction(), `this` refers to the global object (or undefined in strict mode). When called as a method of myObject, `this` refers to myObject.

**Arrow Function 'this' Context**
Arrow functions do not have their own `this` context. Instead, they capture the `this` value of the enclosing context at the time they are created. This is known as lexical scoping of `this`.

```javascript
const myObject = {
  myMethod: () => {
    console.log(this);
  },
};

const anotherFunction = myObject.myMethod;
anotherFunction(); // 'this' is lexically bound to the enclosing context, not 'myObject'
myObject.myMethod(); // Still lexically bound, not 'myObject'
```

In this example, myMethod is an arrow function. It doesn’t matter how or where we call myMethod; `this` inside of it is always bound to the context in which it was defined, not how it was called. In a browser environment, `this` typically means the global window object.

The value of `this` in the arrow function is determined at the time of declaration and never changes. So call, apply, bind cannot change the value of the arrow function `this`.

**6. No Duplicate Named Parameters 🍀**

Regular functions allow duplicate named parameters, especially in non-strict mode, but arrow functions strictly disallow this, making them more predictable in behavior when dealing with parameters.

```javascript
function regularFunction(a, a) {
  console.log(a); // No error in non-strict mode
}
const arrowFunction = (a, a) => {
  console.log(a); // Syntax error
};
```

**7. It cannot be used as a Generator function 🌈**

`Generator functions` in JavaScript are a special class of functions that can pause execution and resume at a later point. This is achieved using the function\* syntax and the yield keyword. However, this feature is not available with arrow functions.

**Regular Function as Generator**
Regular functions can be declared as generator functions, which enables them to yield multiple values over time, each time they are resumed.

```typescript
function* numberGenerator() {
  yield 1;
  yield 2;
  yield 3;
}

const generator = numberGenerator();

console.log(generator.next().value); // Outputs: 1
console.log(generator.next().value); // Outputs: 2
console.log(generator.next().value); // Outputs: 3
```

In this example, each call to generator.next() resumes the function execution and yields the next number. This is a powerful feature for scenarios like lazy evaluation or handling streams of data.

**Arrow Functions Cannot Be Generators**

Arrow functions, by their design, cannot be used as generator functions. They are intended for concise function expressions and do not support the function\* syntax or the yield keyword.

```javascript
// This will throw a Syntax Error:
const numberGenerator = *() => {
    yield 1;
};

```
If you try to create a generator function using an arrow function syntax, it results in a syntax error. This limitation is due to the nature of arrow functions being syntactically simpler and not supporting advanced features like generators.

**Conclusion 🌱**

Grasping the differences between regular and arrow functions in JavaScript is crucial for writing efficient, clean, and modern code. This article explored these differences, aiding you in choosing the appropriate function type for your coding requirements. Whether you're implementing complex logic or simply scripting a basic functionality, understanding these nuances ensures your JavaScript code is up to par with contemporary standards.

Happy Coding!!!