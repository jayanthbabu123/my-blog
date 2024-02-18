+++
title = 'Es6 Features Introduction - Let and Const - Lession 21'
date = 2024-02-15T20:34:19+05:30
draft = false
+++

## Introduction

ECMAScript 6, also known as ES6 and ECMAScript 2015, is a significant update to the JavaScript language since its inception. Released in June 2015, ES6 brought a fresh syntax for better readability and more efficient coding, along with new features aimed at addressing the common issues faced by JavaScript developers. The goal was to make JavaScript development smoother and more modern, catering to the needs of complex applications and libraries.

In the past, JavaScript developers relied on the `var` keyword to declare variables. However, `var` can have unintended consequences due to its behavior. `ES6` introduced `let` and `const` as much better alternatives, making your code cleaner and less likely to have hidden bugs.

## let and const

In the quest for writing cleaner and more predictable JavaScript code, ES6 (ECMAScript 2015) introduced two new ways to declare variables: let and const. These keywords address some of the inherent issues with the traditional var keyword.

let and const serve a similar purpose in declaring variables. The key difference lies in that const is used to declare variables whose values should remain constant and not be reassigned.

## Differences between var, let, and const

## 1. Scoping

`var:` Function-scoped (or globally-scoped if declared outside a function). This means variables declared with var are accessible anywhere within their function, or globally if not inside a function.

`let and const:` Block-scoped. Variables declared with let or const are only accessible within the block of code in which they are defined. A block is commonly denoted by curly braces {}, such as in if statements, for loops, etc.

The primary advantage of `let` and `const` lies in their block-level scoping. Unlike `var`, variables declared with let or const exist only within the specific block of code where they are defined. Here's how this applies to different block structures:

**1. if statements**

```javascript
if (true) {
  let message = "Inside the if block";
  console.log(message); // Output: "Inside the if block"
}
console.log(message); // ReferenceError: message is not defined
```

**2. for loops**

```javascript
for (let i = 0; i < 3; i++) {
  console.log(i); // Output: 0, 1, 2
}
console.log(i); // ReferenceError: i is not defined
```

**3. while loops**

```javascript
let count = 0;
while (count < 5) {
  console.log(count); // Output: 0, 1, 2, 3, 4
  count++;
}
console.log(count); // Output: 5 (count remains accessible)
```

**4. Standalone blocks**

```javascript
{
  let secret = "This variable is hidden";
  console.log(secret); // Output: "This variable is hidden"
}
console.log(secret); // ReferenceError: secret is not defined
```

**5. Nested blocks**

```javascript
{
  let secret = "This variable is hidden";
  {
    let secret = "This variable is also hidden";
    console.log(secret); // Output: "This variable is also hidden"
  }
  console.log(secret); // Output: "This variable is hidden"
}
console.log(secret); // ReferenceError: secret is not defined
```

## 2. Hoisting: A Matter of Timing

In JavaScript, hoisting is a mechanism that conceptually moves variable and function declarations to the top of their scope before code execution. However, the specifics of how hoisting works differ between var, let, and const.

`var:` Variables declared with var are fully hoisted to the top of their function (or global scope if outside a function). This means you can technically access them before their line of declaration. However, remember that only the declaration is hoisted, not the initialization. Therefore, accessing a var variable before its assignment will result in undefined.

`let and const:` Variables declared with let and const are also hoisted, but they reside in a "Temporal Dead Zone" (TDZ) until their declaration line is reached in the code execution. Attempting to access let or const variables within the TDZ results in a ReferenceError.

**Example: Understanding Hoisting Behavior**

```javascript
function hoistingExample() {
  console.log(varVariable); // Output: undefined
  console.log(letVariable); // ReferenceError: letVariable is not defined
  console.log(constVariable); // ReferenceError: constVariable is not defined

  var varVariable = "I'm hoisted (var)";
  let letVariable = "I'm in the TDZ (let)";
  const constVariable = "I'm in the TDZ too (const)";
}

hoistingExample();
```

Prefer let and const to avoid confusion caused by traditional var hoisting. Understanding the Temporal Dead Zone is critical for writing robust ES6 code.

## 3. Re-declaration: The Rules of Repetition

In ES6, how you declare a variable impacts whether or not you can declare it again with the same name within the same scope:

**var: Forgiving**

You can re-declare variables using var multiple times within the same scope. The latest declaration will always win.

```javascript
var myName = "John";
var myName = "Jane"; // This is fine, 'myName' is now "Jane"
```

**let: Strict**

You cannot re-declare a let variable within the same block of code. Attempting to do so will throw an error.

```javascript
let age = 25;
let age = 30; // This will cause an error
```

**const: Unchangeable**

const variables cannot be re-declared at all. They also cannot be reassigned a new value after their initial declaration.

```javascript
const name = "John";
const name = "Jane"; // This will cause an error
```

let and const help you avoid accidentally overwriting variables, making your code more predictable.

## 4. Updating Variables: Flexibility and Restriction

A key difference between var, let, and const lies in their ability to be updated after their initial declaration.

**var and let: Mutable**

Variables declared with `var` and `let` can have their values changed (i.e., updated) as needed throughout your code. This provides flexibility when the value of a variable needs to evolve.

```javascript
var count = 0;
count = count + 1; // Updating the value of 'count'

let message = "Hello";
message = message + ", world!"; // Updating 'message'
```

**const: Immutable by Default**

Variables declared with `const` cannot have their values directly reassigned. This means once you assign a value to a `const` variable, that value becomes a fixed part of its identity. Trying to change it will result in an error.

```javascript
const PI = 3.14;
PI = 3.1515; // Error: Not allowed to change a 'const'
```

In modern JavaScript, favor const for variables that don't need to change. Use let for variables that require updating. This practice improves code readability and protects you from unintended alterations.

## 5. Updating Objects and Arrays: The Flexibility of const

It's important to understand that declaring an array or object with const doesn't make it entirely unchangeable. Here's the key distinction:

What's Constant: Using const means you cannot reassign the variable to point to a completely different array or object. The variable will always hold a reference to the original structure.

What's Changeable: You are free to modify the contents of the array (add, remove, change elements) or update the properties of an object. Think of the const variable as a handle to a container—you can't replace the container, but you can alter what's inside it.

```javascript
const colors = ["red", "green", "blue"];
colors.push("yellow"); // Allowed: Modifying the array
console.log(colors); // Output: ["red", "green", "blue", "yellow"]

const person = { name: "Alice", age: 25 };
person.city = "New York"; // Allowed: Updating a property
console.log(person); // Output: { name: "Alice", age: 25, city: "New York" }

colors = ["purple"]; // Error: Can't reassign a new array to 'colors'
person = {}; // Error: Can't reassign a new object to 'person'
```

Choose const as a default even for arrays and objects. It promotes more organized code while providing the freedom to manage your data as needed.

## Conclusion

`ES6` introduced `let` and `const` to give developers better control over their variables compared to the traditional `var`. They help you write cleaner and less error-prone code by ensuring variables are only accessible where they're intended and their values are managed in a predictable way.

A good rule of thumb is to always start by declaring variables with const. This provides safety because you know the value won't be accidentally reassigned. If you later discover that you need to update the value, then switch to using let. In most new JavaScript projects, there's rarely a need to use var due to its potential for `scoping` and `hoisting` issues.

Choosing const and let as your go-to variable declaration keywords results in more organized, understandable, and reliable JavaScript code.
