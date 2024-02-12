+++
title = 'Throttling in Javascript'
date = 2024-02-09T22:17:28+05:30
draft = false
+++

Throttling in JavaScript is a technique used to limit the frequency at which a function is called. Unlike debouncing, which delays the function call until after a certain amount of time has elapsed since the last call, throttling ensures that a function is called at most once every specified number of milliseconds. This is particularly useful for handling events that you want to allow to happen periodically, but not as frequently as they are triggered, such as scrolling or resizing a window.

This method ensures that the function is not executed more often than the specified rate, regardless of how many times the event that triggers it occurs.

Here's an example of how to implement a basic throttling function in JavaScript:

In JavaScript:

```javascript
function throttle(func, limit) {
  let inThrottle;
  return function () {
    const args = arguments;
    const context = this;
    if (!inThrottle) {
      func.apply(context, args);
      inThrottle = true;
      setTimeout(() => (inThrottle = false), limit);
    }
  };
}

// Usage example: Throttling a window resize event
function handleResize() {
  console.log("Window is resizing");
}

window.addEventListener("resize", throttle(handleResize, 1000));
```

In this example, throttle is a higher-order function that takes a function func and a time limit limit as arguments. It returns a new function that, when invoked, checks if it's been called within the limit period. If it has, the call is ignored; if not, the function is executed, and the timer starts. This ensures that handleResize is not called more than once every 1000 milliseconds (1 second), regardless of how many resize events occur.

This throttling mechanism is useful for optimizing performance by controlling how often resource-intensive operations are executed in response to frequent events.

