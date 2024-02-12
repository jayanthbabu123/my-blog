+++
title = 'Closures in Javascript'
date = 2024-02-09T13:21:55+05:30
draft = false
+++

# What is Closure?

A closure is a feature in JavaScript where an inner function has access to the outer (enclosing) function's variables—a scope chain. The closure has three scope chains: it has access to its own scope (variables defined between its curly brackets), it can access the outer function's variables, and it can access the global variables.

The power of a closure is that it remembers the environment in which it was created, even after the outer function has completed execution.

## Example - 1

```javascript
let globalVar = "I am a global variable";

function outerFunction() {
  let outerVar = "I am an outer variable";

  function innerFunction() {
    let innerVar = "I am an inner variable";
    console.log(innerVar); // Access to its own scope
    console.log(outerVar); // Access to the outer function's variables
    console.log(globalVar); // Access to the global variables
  }

  return innerFunction;
}

let myClosure = outerFunction(); // Executes outerFunction, returns innerFunction
myClosure(); // Executes innerFunction, which is now a closure
```

When you run this JavaScript code, `myClosure()` will access and print variables from its own scope, the outer function's scope, and the global scope, demonstrating how closures work in terms of scope chain.

# Example 2 - Private Variables

Here's a simple example of using closures to create a private counter that can be incremented by calling a function repeatedly. This pattern is useful for encapsulating state (the counter) in a way that it cannot be accessed or modified directly from outside the closure, providing a measure of data privacy and security.

```javascript
function createCounter() {
  let counter = 0;

  function increment() {
    counter++;
  }

  return increment;
}

let counter = createCounter();
counter(); // 1
counter(); // 2
counter(); // 3

let counter2 = createCounter();
counter2(); // 1
counter2(); // 2

let counter3 = createCounter();
counter3(); // 1
counter3(); // 2
counter3(); // 3
```

The provided code snippet illustrates a closure in JavaScript, where a createCounter function encapsulates a private counter variable that is incremented through a returned increment function. Each time createCounter is invoked, it creates an independent instance of this increment function, which has access to its own counter variable. This mechanism ensures that the counter is not accessible from outside the closure, effectively encapsulating and protecting the counter's state. Through closures, JavaScript allows for the creation of functions with private variables like counter, which can be manipulated only through designated functions, providing a layer of abstraction and security for managing internal state.

## Example - 3 - Module Pattern

The Module Pattern in JavaScript is a design pattern that uses closures to create private and public sections within a module. This approach helps in organizing code, managing dependencies more efficiently, and keeping the global namespace clean by avoiding global scope pollution.

```javascript
let moduleA = (function () {
  let privateCounter = 0;
  function changeBy(val) {
    privateCounter += val;
  }

  return {
    increment: function () {
      changeBy(1);
    },

    decrement: function () {
      changeBy(-1);
    },

    value: function () {
      return privateCounter;
    },
  };
})();

moduleA.increment(); // 1
moduleA.increment(); // 2
moduleA.decrement(); // 1
moduleA.value(); // 1
```

This JavaScript snippet illustrates the Module Pattern through the creation of moduleA, which manages a private counter. The pattern enables encapsulation of the counter's value, preventing direct external modification while allowing controlled interaction through the module's public interface.

Inside moduleA, a privateCounter variable and a changeBy function are defined, both inaccessible from outside the module. The changeBy function is a private utility that adjusts the privateCounter by a specified value. The module exposes three methods: increment, decrement, and value. These methods provide controlled ways to modify and access the privateCounter:

- increment: Increases the privateCounter by 1.
- decrement: Decreases the privateCounter by 1.
- value: Returns the current value of privateCounter.

This setup ensures that privateCounter can only be modified using the increment and decrement functions and can be read using the value function. By invoking these methods, moduleA demonstrates how the Module Pattern supports both encapsulation—keeping privateCounter shielded from direct access—and interaction, allowing external code to influence and read the counter in a controlled manner. This pattern is particularly useful for creating structured, maintainable code with clear separation between a module's internal state and its external interface.


