+++
title = 'Promises in Javascript Lession 20'
date = 2024-02-04T23:39:05+05:30
draft = false
categories = ['Javascript Learning']
image= "/images/js-promises.webp"
tags=[
    "Javascript",
    "Javascript Promises",
    "Web Development",
    "Frontend Development",
    "Promises",
    "Javascript Promises",
    "Promises"

]
weight = 20
+++

![Promises Lession 20](/images/js-promises.webp)

## Introduction

Promises in JavaScript are a powerful way to handle asynchronous operations. They represent a value that may be available now, in the future, or never at all. Promises allow you to attach callbacks to handle the fulfillment or rejection of asynchronous actions. This approach greatly simplifies asynchronous programming by making the code more readable and easier to debug.

## Creating a Promise

A Promise is created using the Promise constructor, which takes a function called the executor. The executor function is executed immediately by the Promise implementation, and it receives two functions as arguments: resolve and reject. The resolve function is called when the asynchronous task completes successfully, while the reject function is called if an error occurs.

```javascript
const myPromise = new Promise((resolve, reject) => {
  // Asynchronous operation code here
});
```

## Example Without Promise: setTimeout

Let's consider a simple example to illustrate how a function containing setTimeout behaves without promises:

```javascript
function delayedOperation() {
  setTimeout(() => {
    console.log("Operation completed after 2 seconds");
    return "Success";
  }, 2000);
}

const result = delayedOperation();
console.log(result); // This will log `undefined`
```

In this example, the delayedOperation function uses setTimeout to simulate an asynchronous operation that completes after 2 seconds. However, since setTimeout is non-blocking, the function returns undefined immediately, before the timeout callback is executed.

This can be solved in two primary ways: using callbacks and using Promises.

## Example With Callback

A callback is a function passed into another function as an argument, which is then invoked inside the outer function to complete some kind of routine or action.

Here's how we can modify the setTimeout example to use a callback:

```javascript
function delayedOperationCallback(callback) {
  setTimeout(() => {
    callback("Success");
  }, 2000);
}

delayedOperationCallback((result) => {
  console.log(result); // This will log "Success" after 2 seconds
});
```

In this example, the delayedOperationCallback function takes a callback function as an argument. It then calls this callback with the result "Success" after 2 seconds.

## Using Promises

As shown in the previous section, using Promises provides a more structured approach to handling asynchronous operations. Here's the Promise example again for comparison:

```javascript
function delayedOperationWithPromise() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("Success");
    }, 2000);
  });
}

delayedOperationWithPromise()
  .then((result) => {
    console.log(result); // This will log "Success" after 2 seconds
  })
  .catch((error) => {
    console.error(error);
  });
```

## Why Promises Are a Cleaner Approach

While callbacks provide a way to handle asynchronous operations, they come with several drawbacks, especially when dealing with multiple asynchronous tasks. This can lead to what is commonly referred to as "callback hell" or the "pyramid of doom," where you end up with a tangled mess of nested callbacks, making the code hard to read and maintain.

Promises offer a cleaner and more manageable solution for several reasons:

**Chaining:** Promises can be chained, meaning you can perform multiple asynchronous operations back to back, with each operation starting when the previous one completes. This is done using .then() methods, making the code more readable and easier to follow.

**Error Handling:** With callbacks, error handling must be done manually within each callback. Promises simplify this with the .catch() method, allowing you to handle errors in one place, even for errors that occur in a chain of promises.

**State:** A promise has a clear state (`pending`, `fulfilled`, or `rejected`), making the flow of asynchronous operations easier to reason about.

While callbacks are a fundamental part of JavaScript and still useful in many scenarios, Promises provide a more powerful and flexible way to handle asynchronous operations. They allow for better structuring of asynchronous code, easier error handling, and cleaner syntax, especially with the addition of async/await syntax in ES2017, which builds on promises for even more readable asynchronous code. This evolution from callbacks to Promises (and async/await) demonstrates a significant step forward in JavaScript's ability to handle asynchronous operations in a more efficient and less error-prone way.

## Methods of Promises in JavaScript

Promises in JavaScript are a powerful tool for handling asynchronous operations. They offer several methods that allow for more flexible, clean, and manageable asynchronous code. Here's a detailed look at these methods with examples:

## .then method

The .then method allows you to specify a callback function that will be executed once the promise is resolved. This method is used to handle success cases in asynchronous code.

```javascript
const promise = new Promise((resolve, reject) => {
  setTimeout(() => resolve("Resolved after 2 seconds"), 2000);
});

promise.then(
  (result) => console.log(result), // Logs "Resolved after 2 seconds"
  (error) => console.log(error)
);
```

In this example, the .then method takes two arguments: first callback function will be executed if the promise is resolved, and second callback function will be executed if the promise is rejected.

## .catch method

The .catch method allows you to specify a callback function that will be executed once the promise is rejected. This method is used to handle error cases in asynchronous code.

```javascript
const promise = new Promise((resolve, reject) => {
  setTimeout(() => reject("Rejected after 2 seconds"), 2000);
});

promise
  .then(result => console.log(result))
  .catch(error => console.log(error)); // Logs "Rejected after 2 seconds"

```

In this example, the .catch method takes one argument: a callback function that will be executed if the promise is rejected.

## .finally method
This method is similar to the `.then` method, but it is executed regardless of the state of the promise. This method is used to handle success and error cases in asynchronous code.

```javascript
const promise = new Promise((resolve, reject) => {
  setTimeout(() => resolve("Resolved after 2 seconds"), 2000);
});

promise
  .then(result => console.log(result)) // Logs "Resolved after 2 seconds"
  .catch(error => console.log(error))
  .finally(() => console.log("Operation completed")); // Logs "Resolved after 2 seconds" and "Operation completed"

```

In this example, the .finally method takes one argument: a callback function that will be executed regardless of the state of the promise.






