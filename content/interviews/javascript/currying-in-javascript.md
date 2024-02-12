+++
title = 'Currying in Javascript'
date = 2024-02-09T14:24:31+05:30
draft = false
+++

In JavaScript, currying is a technique that involves transforming a function that takes multiple arguments into a sequence of functions, each taking a single argument. Think of it as a way to break down a function that takes many ingredients into smaller steps, where each step takes one ingredient and gives you something that can take the next one until the dish is complete.

For example, if you had a function to add three numbers, traditionally, you might write it to take all three numbers at once:

```javascript
function add(a, b, c) {
  return a + b + c;
}
```

With currying, you would instead create a function that takes one number, then returns another function that takes the next number, and so on:

```javascript
function add(a) {
  return function (b) {
    return function (c) {
      return a + b + c;
    };
  };
}
```

To use this curried `add` function, you would call it like this:

```javascript
const result = add(1)(2)(3); // returns 6
```

This method helps make things simpler to understand and use. It's a trick that's also used in some JavaScript libraries like d3.js to make coding easier and more flexible.
