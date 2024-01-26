+++
title = 'Javascript Functions- Lession 6'
date = 2024-01-26T15:27:30+05:30
draft = false
categories = ['Javascript Learning']
image= "/images/functions-javascript.webp"
tags=[
    "Javascript",
    "Functions",
    "Javascript Functions",
    "Web Development",
    "Frontend Development",
    "Javascript Basics",
    "Javascript Syntax",
    "Javascript Types",
]
weight = 6
+++

![Javascript Functions Lession 6](/images/functions-javascript.webp)

### 1. Introduction 🌱

A function in JavaScript is a block of code designed to perform a particular task. It is a fundamental building block in JavaScript, allowing you to execute the same code multiple times without rewriting it. Functions are useful for organizing and reusing code, making programs more modular and efficient.

## 2. How to Write a Function 📝

A JavaScript function is defined with the `function` keyword, followed by a function name, followed by parentheses () and then curly braces {}:

```javascript
function functionName(param1, param2) {
  // code to be executed
}
```

**Begin with the function Keyword:** This keyword is used to start the declaration of a function.

**Choose a Function Name:** This should follow the naming rules similar to variables - use letters, digits, underscores, and dollar signs. The name should be descriptive of what the function does.

**Declare Parameters:** Inside the parentheses (), list any parameters the function will use, separated by commas. Parameters are like placeholders for the values (arguments) that will be passed to the function when it's called.

**Write the Function Body:** Enclosed in curly brackets {}, this is where the code that defines the function's actions goes. Here, you can use the parameters as local variables.

**Calling the Function:** To execute the function, use its name followed by parentheses. If the function requires parameters, pass the arguments inside these parentheses.

```javascript
functionName(param1, param2);
```

In the example above, `functionName` is the name of the function and `param1` and `param2` are the parameters that the function will use.

## 3. Ways to Write a Function in JavaScript 🌿

There are several ways to define functions in JavaScript, each with its own characteristics and use cases. Let's delve into three primary methods: Function Declarations, Function Expressions, and Immediately Invoked Function Expressions (IIFE).

### 3.1. Function Declarations 🍀

A Function Declaration defines a named function. The key feature of a Function Declaration is its ability to be hoisted, meaning it can be called before it is defined in the code.

```javascript
function greet(name) {
  return `Hello, ${name}!`;
}
```

In this example, `greet` is a function that takes `name` as a parameter and returns a greeting string.

### 3.2. Function Expressions 🌵

A Function Expression defines a function as a part of an expression, typically assigning it to a variable. Unlike Function Declarations, they are not hoisted, so they cannot be called before they are defined.

```javascript
var greet = function (name) {
  return `Hello, ${name}!`;
};
```

In this example, `greet` is a variable that stores a function that takes `name` as a parameter and returns a greeting string.

### 3.3. Immediately Invoked Function Expressions (IIFE) 🌴

An IIFE is a Function Expression that is executed immediately after it is defined. It is often used to create a private scope, protecting variables and methods from being accessed from outside the function.

```javascript
(function (name) {
  console.log(`Hello, ${name}!`);
})("World");
```

In this example, `Hello, World!` is logged to the console.

**Differences and Best Practices**

**Hoisting:** Function Declarations are hoisted (i.e., their definitions are lifted to the top of their scope). This means they can be called before they are defined in the script. In contrast, Function Expressions are not hoisted.

**Scoping:** IIFEs are often used to create private scopes. By enclosing the function and its invocation in parentheses, it prevents polluting the global scope with variables and function names.

**Use Cases:**

Function Declarations are best when you need to define a function that can be called throughout your script, regardless of where it’s defined.
Function Expressions are ideal when a function needs to be assigned as a value, passed as an argument to another function, or when choosing between function definitions conditionally. IIFEs are suitable for executing a function immediately while keeping variables out of the global scope. This can be beneficial in modular code patterns.

## 4. The Scope of Variables 🌐

**Global Scope:** Variables declared outside a function are global and can be accessed anywhere in your code.

```javascript
let globalVar = "I am global";

function testScope() {
  console.log(globalVar); // Accessible here
}
```

**Local Scope:** Variables declared inside a function are local to that function and cannot be accessed outside of it.

```javascript
function testScope() {
  let localVar = "I am local";
}
console.log(localVar); // Unreachable, will cause an error
```

## 5. Return Statement 🔙

The return statement ends function execution and specifies a value to be returned to the function caller.

Any code written after the return statement in a function is not executed.

```javascript
function sum(a, b) {
  return a + b;
  console.log("This will not be executed");
}
```

## 6. Incorrect Parameters and Return Values ❓

Accessing a function with incorrect parameters can lead to unexpected results, as JavaScript doesn't enforce the number and type of arguments.

```javascript
function sum(a, b) {
  return a + b;
}

sum(10); // Returns NaN, because b is undefined
```

## 7. Accessing a Function Without () ❗

Accessing a function without () returns the function definition, not the result of the function.

```javascript
function greet() {
  return "Hello World!";
}

console.log(greet); // Outputs the function definition
```

### 8. Function Calls Without a Return Statement 🚫

When a function in JavaScript is called but does not have a return statement, it processes the code inside it but returns undefined. This is the default behavior for functions without a return value.

```javascript
function greet(name) {
  console.log(`Hello, ${name}!`);
}

let result = greet("Alice");
console.log(result); // Output: undefined
```

## Conclusion 💚

In summary, functions in JavaScript are essential for code reusability and organization. Understanding different ways of defining functions, scope of variables, return statements, and how functions handle parameters is crucial for effective JavaScript programming. This foundational knowledge sets the stage for more advanced topics such as closures, callbacks, and asynchronous programming in JavaScript.
