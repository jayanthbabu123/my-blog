+++
title = 'Memoization in Javascript'
date = 2024-02-10T14:51:58+05:30
draft = false
+++

Memoization is an optimization technique that stores the results of expensive function calls and reuses those results when the same inputs occur again, thereby avoiding the need for repeated computations. This is particularly useful in scenarios involving heavy computational tasks, like recursive algorithms or data processing functions.

## How to Implement:

You can create a memoized function by making a function that remembers the outcomes of previous inputs. Here's a simple example using a function that adds two numbers:

```javascript
function memoizeAdd() {
  let cache = {};
  return function (a, b) {
    let key = `${a},${b}`;
    if (cache[key]) {
      return cache[key]; // Return cached result
    } else {
      let result = a + b;
      cache[key] = result; // Store result in cache
      return result;
    }
  };
}

const memoizedAdd = memoizeAdd();
console.log(memoizedAdd(5, 2)); // Computes and caches result
console.log(memoizedAdd(5, 2)); // Retrieves result from cache
```

In this example, we create a memoizeAdd function that uses a cache object to remember the sums of numbers it has already added. When you call memoizedAdd with two numbers, it first checks if the sum of those numbers is in the cache. If it is, it returns the cached result, skipping the computation. If not, it calculates the sum, stores it in the cache, and then returns the result. This way, repeated calls with the same inputs are much faster because they avoid unnecessary calculations.
