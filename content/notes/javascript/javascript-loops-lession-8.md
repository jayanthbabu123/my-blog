+++
title = 'Javascript Loops - Lession 8'
date = 2024-01-26T21:20:00+05:30
draft = false
categories = ['Javascript Learning']
image= "/images/js-loops.webp"
tags=[
    "Javascript",
    "Loops",
    "Javascript Loops",
    "Web Development",
    "Frontend Development",
    "Javascript Basics",
    "Javascript Syntax",
    "Javascript Types",
]
weight = 8
+++

![Javascript Loops Lession 8](/images/js-loops.webp)

## Introduction 🌱

Loops are a fundamental part of JavaScript programming, allowing you to execute a block of code repeatedly under certain conditions. They are essential for tasks that require repetitive actions, such as iterating over arrays or processing data. In this overview, we will cover three types of loops:

1. for Loop
2. for of Loop
3. for in Loop

### 🎡 1. The for Loop

The for loop is one of the most commonly used loops in JavaScript. It is used to execute a code block several times, with new values in each iteration. The loop includes three optional expressions:

```javascript
for (initialization; condition; increment) {
  // code to be executed
}
```

- **initialization:** This is executed once before the loop starts. It's often used for initializing a counter variable.
- **condition:** This is the condition that must be true for the next loop iteration to execute.
- **increment:** This is executed after every loop iteration, typically used to update the counter variable.

Lets discuss some practical examples:

**Counting Loop:**
The counting loop is a classic example of using a for loop to execute a block of code a specific number of times. In this example, the loop iterates five times, logging each iteration number.

```javascript
for (let i = 0; i < 5; i++) {
  console.log(i);
}
// Output: 0, 1, 2, 3, 4
```

This loop initializes a variable `i` to `0` and increments it by `1` in each iteration (`i++`). The loop continues until `i` is less than `5`. As a result, it logs the numbers `0` to `4`. This kind of loop is commonly used for executing a code block a known number of times.

**Decrementing Loop:**

This loop will count from `5` to `0` in descending order:

```javascript
for (let i = 5; i >= 0; i--) {
  console.log(i);
}
// Output: 5, 4, 3, 2, 1, 0
```

**Iterating Over an Array:**
This example demonstrates how to use a `for` loop to iterate through each element of an array. The loop runs for the length of the array, providing access to each array element.

```javascript
let fruits = ["apple", "banana", "mango"];
for (let i = 0; i < fruits.length; i++) {
  console.log(fruits[i]);
}
// Output: apple, banana, mango
```

In this snippet, `fruits.length` provides the number of elements in the fruits array. The loop starts with `i = 0` and runs until `i` is less than the number of `fruits`. Each iteration logs the current fruit (`fruits[i]`) to the console, resulting in each fruit being printed out. This method is particularly useful for arrays where you need to access each element by its index.

### 2. The for/of Loop 🌐

Introduced in `ES6 (2015)`, the `for/of` loop provides a simpler and cleaner way to iterate over iterable objects like `Arrays`, `Strings`, `Maps`, and `NodeLists`.

Syntax:

```javascript
for (var variable of iterable) {
  // code to be executed
}
```

**Variable:** In each iteration, the value of the next property is assigned to this variable. It can be declared with `const`, `let`, or `var`.

**Iterable:** An object that has iterable properties.

lets discuss some practical examples:

**1. Looping Over an Array**

The `for/of` loop provides a clean and straightforward way to iterate over array elements. In this example, we use it to loop through an array of colors.

```javascript
let colors = ["red", "green", "blue"];
for (var color of colors) {
  console.log(color);
}

// Output: red, green, blue
```

In this snippet, `color` represents each element in the `colors` array during the loop's iterations. The loop automatically iterates over each element, assigning color to each array element in turn and logging it to the console. This approach is much cleaner than using a traditional for loop with indexing, especially when you don't need to know the index of each element.

**2. Looping Over a String**

The for/of loop is also useful for iterating over strings, allowing you to perform operations on each character.

```javascript
let greeting = "Hello";
for (var char of greeting) {
  console.log(char);
}

// Output: H, e, l, l, o
```

In this example, the `for/of` loop iterates through each character in the string greeting. The loop assigns each character to the `char` variable and logs it to the console. This approach is useful when you need to perform operations on each character of the string.

### 3. The for/in Loop 🌟

Introduced in `ES6 (2015)`, the `for/in` loop in JavaScript is used to iterate over the properties of `Objects`.

Syntax:

```javascript
for (var variable in object) {
  // code to be executed
}
```

lets discuss some practical examples:

**1. Looping Over an Object**

The `for/in` loop is ideal for accessing each property in an object. Here's an example of iterating over the properties of a person object:

```javascript
let person = {
  name: "John",
  age: 30,
  city: "New York",
};
for (var property in person) {
  console.log(property + ": " + person[property]);
}

// Output: name: John, age: 30, city: New York
```

**2. Looping over Arrays**

The `for/in` loop is also useful for looping over arrays. Here's an example of iterating over the elements of an array:

```javascript
let colors = ["red", "green", "blue"];
for (var color in colors) {
  console.log(colors[color]);
}

// Output: red, green, blue
```

The `for/in` loop is an essential tool for working with objects in JavaScript. It provides an efficient way to loop through properties of an object, which is especially useful for operations involving the dynamic retrieval and manipulation of object properties.

**Limitations of the for/in Loop for Arrays**

While the `for/in` loop is useful for iterating over object properties, it's not ideal for arrays due to several limitations:

**Unpredictable Index Order:** The `for/in` loop does not guarantee the order of array elements, which can be problematic if your logic depends on processing elements in order.

**Iterates Over Non-Element Properties:** It includes all enumerable properties, not just the array elements. This includes inherited properties and any additional properties added to the array object.

**Slower Performance:** The `for/in` loop is generally slower than other loops like for or for/of when iterating over arrays, as it checks each property to determine if it's an array element.

### Adding Break and Continue in JavaScript Loops

In addition to the various types of loops (`for`, `for/of`, `for/in`), understanding the use of break and continue statements in loops is crucial. These statements provide more control over the flow of loops.

## 🛑 Break Statement

The break statement is used to exit a loop before it has finished its natural course. This is particularly useful if you need to stop the execution of the loop when a certain condition is met.

```javascript
for (let i = 0; i < 10; i++) {
  if (i === 5) {
    break; // Exits the loop when i is 5
  }
  console.log(i);
}
```

In this example, the loop is designed to run from 0 to 9. However, when i becomes 5, the break statement is executed, causing the loop to terminate prematurely. The console will log numbers 0 to 4.

## ⏭️ Continue Statement

The continue statement is used to skip the current iteration of a loop and continue with the next iteration. This is useful when you want to avoid certain values or conditions within a loop but still continue the loop's execution.

```javascript
for (let i = 0; i < 10; i++) {
  if (i === 5) {
    continue; // Skips the current iteration
  }
  console.log(i);
}
```

In this loop, when `i` is equal to `5`, the continue statement is executed. This causes the loop to skip the current iteration (so `5` is not logged to the console) and continue with the next iteration. The console will log numbers `0` to `4` and then `6` to `9`.

## Conclusion 📚

Loops in JavaScript are powerful tools for executing repetitive tasks efficiently. The `for`, `for/of`, and `for/in` loops each serve different purposes and can be applied in various scenarios to simplify code and enhance performance. Understanding and applying these loops appropriately is a key skill in JavaScript programming.
