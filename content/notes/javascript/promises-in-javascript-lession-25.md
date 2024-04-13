+++
title = 'Understanding Promises in JavaScript - Lession 25'
date = 2024-04-13T17:39:53+05:30
draft = false
+++

In web development, managing tasks that take some time to complete, like data fetching or setting timers, is crucial. Initially, these tasks were handled using callbacks, which often led to complex and difficult-to-manage code. To address these issues, JavaScript introduced a feature called "Promises" that simplified executing asynchronous tasks.

## Early Challenges with Asynchronous Operations

Let’s look at a common issue when trying to directly return a value from a function that uses `setTimeout`, a method for delaying operations:

```javascript
function fetchMessage() {
  let message;
  setTimeout(() => {
    message = "Hello, this message is delayed";
  }, 3000);
  return message;
}

console.log(fetchMessage()); // Outputs: undefined
```

This function returns `undefined` because setTimeout does not stop the function’s execution to wait for the timeout. The function completes before setTimeout can update the message variable.

## Callbacks in JavaScript

Callbacks are functions passed as arguments to other functions to be executed after a certain event occurs or a particular operation completes. This approach was commonly used to handle tasks that do not produce immediate results, such as data fetching or timers.

The primary purpose of a callback is to ensure that certain code does not execute until another operation has finished, providing a basic form of control over asynchronous operations. However, extensive use of callbacks can lead to nested or deeply indented code, often referred to as `"callback hell,"` which complicates understanding and maintaining the code.

Here’s a practical example demonstrating the use of callbacks for a simple asynchronous operation:

```javascript
function delayedMessageCallback(callback) {
  setTimeout(() => {
    callback("Hello, this message is displayed after 3 seconds");
  }, 3000);
}

delayedMessageCallback((message) => {
  console.log(message); // Outputs after 3 seconds: Hello, this message is displayed after 3 seconds
});
```

In this example, delayedMessageCallback takes a function as an argument, referred to as the callback. This function is then called inside setTimeout after a delay of 3 seconds. When setTimeout completes, it triggers the callback function, which executes the code to log the message to the console.

While this approach works for simple cases, managing multiple callbacks can become challenging. It can lead to a situation where callbacks are nested within callbacks, creating complex chains that are hard to follow and debug. This is why the introduction of Promises and later, async/await, has been a significant improvement, providing more straightforward ways to structure asynchronous code.

## The Introduction of Promises

Promises were introduced in ECMAScript 2015 (also known as ES6) and provide a more manageable method for handling asynchronous operations. A Promise is an object that represents a value which may not yet be available but will be resolved or rejected at some point in the future.

A Promise has three states:

`Pending:` The initial state of a Promise. The outcome is not yet known.

`Fulfilled:` The state of a Promise representing a successful operation.

`Rejected:` The state of a Promise representing a failed operation.

Here’s how you create a Promise:

```javascript
let promise = new Promise(function (resolve, reject) {
  // Code to perform the asynchronous operation goes here
});
```

In this setup, `resolve` and `reject` are functions you call to settle the promise once the asynchronous operation completes. If the operation is successful, you call `resolve(value)`, and if an error occurs, you call `reject(error)`.

Using the previous example, we can rewrite it using Promises to handle the asynchronous behavior effectively and include error handling:

```javascript
function delayedMessagePromise() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("Hello, this message is displayed after 3 seconds");
      // Uncomment the following line to simulate an error
      // reject('Failed to deliver message');
    }, 3000);
  });
}

delayedMessagePromise()
  .then((message) => {
    console.log(message); // Outputs after 3 seconds: Hello, this message is displayed after 3 seconds
  })
  .catch((error) => {
    console.error("An error occurred:", error);
  });
```

In this refined example, the `delayedMessagePromise` function returns a Promise. The `setTimeout` is used to simulate an asynchronous operation. If the operation is successful, the Promise is `resolved` with a message. If there's an error (e.g., in case of timeout or server error), the Promise is rejected, and the error can be handled in a `.catch()` block.

Promises have transformed how developers write asynchronous code in JavaScript. By providing a way to manage asynchronous operations in a cleaner and more systematic manner, Promises help avoid the complexities of callback-based coding, making code easier to write, read, and debug.

