+++
title = 'Debouncing in Javascript'
date = 2024-02-09T19:50:32+05:30
draft = false

+++

In JavaScript, debouncing is a technique that involves limiting the rate at which a function is called. It is useful for preventing unwanted function calls that are triggered too frequently. For example, if you're typing in a search box, you might not want to search after every letter you type because it would make too many searches. Instead, you wait until you've stopped typing for a bit and then search.

Here's an example of debouncing a function that logs messages when typing in an input field:

In HTML:

```html
<input type="text" />
```

```javascript
const input = document.querySelector("input");

function debounce(func, wait) {
  let timeout;
  return function () {
    clearTimeout(timeout);
    timeout = setTimeout(func, wait);
  };
}
input.addEventListener("input", debounce(logMessage, 500));

function logMessage() {
  console.log(input.value);
}
```

This debounced function will only log the input field's value if the user stops typing for more than 500 milliseconds, reducing unnecessary function calls and improving performance.
