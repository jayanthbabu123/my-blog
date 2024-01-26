+++
title = 'Javascript Conditions if, else if, switch - Lession 7 🔴🟢'
date = 2024-01-26T18:07:15+05:30
draft = false
categories = ['Javascript Learning']
image= "/images/conditions-javascript.webp"
tags=[
    "Javascript",
    "Conditions",
    "Javascript Conditions",
    "Web Development",
    "Frontend Development",
    "Javascript Basics",
    "Javascript Syntax",
    "Javascript Types",
]
weight = 7
+++

![Javascript Conditions](/images/conditions-javascript.webp)

## Introduction 📘

Conditional statements are a fundamental part of JavaScript, allowing you to perform different actions based on different conditions. These statements control the flow of the code based on boolean conditions - a section of code will only run if the condition is true. Let’s explore the syntax and usage of various conditional statements in JavaScript: `if`, `if/else`, `else if`, and `switch`.

## 1. if Statement 🌟

The if statement is one of the most basic and frequently used conditional statements in JavaScript. It is used to execute a block of code only if a specified condition is true. The if statement evaluates the condition inside its parentheses, and if the condition is truthy, the code block within the curly braces {} is executed.

```javascript
if (condition) {
  // code to be executed if the condition is true
}
```

Here are examples using if conditions with the operators `===`, `!==`, and `>` in JavaScript. Each example demonstrates a different aspect of comparison and logical evaluation.

**1. Using === (Strict Equality Operator)** 🔍

The `===` operator checks for both value and type equality. It's a strict comparison and does not perform type coercion.

```javascript
let favoriteNumber = 7;

if (favoriteNumber === 7) {
  console.log("Yes, 7 is my favorite number!");
}
```

This code will execute the console.log statement because favoriteNumber is exactly equal to 7 in both value and type.

**2. Using !== (Strict Inequality Operator)** ❌

The `!==` operator checks whether two values are not equal in both value and type.

```javascript
let age = 25;

if (age !== 30) {
  console.log("Age is not 30.");
}
```

Here, the code will execute because age is not equal to 30 in value (even though they are of the same type).

**3. Using `>` (Greater Than Operator)** ⬆️

The `>` operator checks if the value on the left is greater than the value on the right.

```javascript
let age = 25;

if (age > 20) {
  console.log("Age is greater than 20.");
}
```

This code will log the message since speed is greater than 30.

**Truthy and Falsy Values in JavaScript ❓**

**Falsy Values 🔴**

In JavaScript, values can be either "truthy" or "falsy". The falsy values are specific and include `0`, `""` (empty string), `null`, `undefined`, `NaN`, and `false`. Any other value in JavaScript is considered truthy.

Let's look at examples with each falsy value:

```javascript
if (false) {
  console.log("This will not run, because false is falsy.");
}

if (0) {
  console.log("This will not run, because 0 is falsy.");
}

if ("") {
  console.log("This will not run, because an empty string is falsy.");
}

if (null) {
  console.log("This will not run, because null is falsy.");
}

if (undefined) {
  console.log("This will not run, because undefined is falsy.");
}

if (NaN) {
  console.log("This will not run, because NaN is falsy.");
}
```

None of these code blocks will execute because each condition is a falsy value.

**Truthy Values** 🟢

Anything that is not in the list of falsy values is truthy. This includes `"non-empty"` strings, any number other than 0, `objects`, `arrays`, `functions`, and the `boolean` true.

```javascript
if (true) {
  console.log("This will run, because true is truthy.");
}

if (42) {
  console.log("This will run, because 42 is truthy.");
}

if ("Hello") {
  console.log("This will run, because a non-empty string is truthy.");
}

if ({}) {
  console.log("This will run, because an object is truthy.");
}

if ([]) {
  console.log("This will run, because an array is truthy.");
}

if (function () {}) {
  console.log("This will run, because a function is truthy.");
}
```

In each of these examples, the condition inside the if statement is truthy, so the corresponding code block will execute.

### 2. if-else Statement ↔️

The if/else statement in JavaScript allows you to execute one block of code if a condition is true and another block if the condition is false. It's an extension of the if statement and is used for binary decision making - do one thing under one condition and something else under an alternative condition.

```javascript
let temperature = 22;

if (temperature > 25) {
  console.log("It's warm outside!");
} else {
  console.log("It's cool outside!");
}
```

In this example, if temperature is greater than 25, the message "It's warm outside!" will be logged to the console. Otherwise, the message "It's cool outside!" will be shown.

**Shortcut: Ternary Operator 🔄**

The ternary operator provides a shorthand way of writing an if/else statement. It takes three operands: a condition, followed by a question mark (?), then an expression to execute if the condition is truthy, followed by a colon (:), and finally the expression to execute if the condition is falsy.

Syntax of Ternary Operator:

```javascript
condition ? expression1 : expression2;
```

```javascript
let score = 75;
let result = score >= 50 ? "Pass" : "Fail";
console.log(result);
```

This code assigns "Pass" to result if score is 50 or higher, and "Fail" if it's lower than 50.

## 3. else if Statement 🎢

The else if statement is used for multiple conditions that are mutually exclusive.

```javascript
let age = 25;

if (age < 18) {
  console.log("You are a minor.");
} else if (age < 65) {
  console.log("You are an adult.");
} else {
  console.log("You are a senior.");
}
```

### 4. Switch Statement 🍃

The `switch` statement is best used when you have multiple possible conditions and you need to execute different code for each condition.

```javascript
let day = new Date().getDay();

switch (day) {
  case 0:
    console.log("Sunday");
    break;
  case 1:
    console.log("Monday");
    break;
  case 2:
    console.log("Tuesday");
    break;
  case 3:
    console.log("Wednesday");
    break;
  case 4:
    console.log("Thursday");
    break;
  case 5:
    console.log("Friday");
    break;
  case 6:
    console.log("Saturday");
    break;
  default:
    console.log("Invalid day");
}
```

### Conclusion 💚

Understanding and correctly implementing conditional statements is vital in JavaScript programming. Each type (`if`, `if/else`, `else if`, `switch`) serves a specific purpose in controlling the flow of logic based on conditions. By mastering these concepts, you can write more efficient, readable, and dynamic JavaScript code, capable of handling a wide range of logical scenarios.
