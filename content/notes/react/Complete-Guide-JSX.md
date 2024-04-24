+++
title = 'Complete Guide on JSX in ReactJS: Lesson-3'
date = 2023-12-30T12:17:19+05:30
weight = 100
draft = true
tags = [
  "ReactJS",
  "JSX",
  "Frontend Development",
  "Web Development",
  "React Components",
  "JSX Syntax",
  "JSX Expressions",
  "React Rendering",
  "React Virtual DOM",
  "React Elements",
  "React Fragments",
  "React Props",
  "React State",
  "React Events",
  "React Conditional Rendering",
  "React List Rendering",
  "React Keys",
  "React Forms",
  "React Lifecycle Methods",
  "React Hooks",
  "React JSX Guide",
  "React JSX Best Practices"
]
categories = ["React-Training"]
image = "https://i.postimg.cc/C5BTXHPd/jsx-react.png"
+++

![JSX in ReactJS](https://i.postimg.cc/C5BTXHPd/jsx-react.png)

### Introduction

JSX, or JavaScript XML, is a unique feature of React that allows developers to write HTML structures directly within JavaScript code. It's a syntax extension that makes writing React components more intuitive and readable. `JSX` provides the flexibility to combine UI templates and JavaScript logic in a single file. In React, you can create `.js` or `.jsx` files to write your components using `JSX`.

### Writing HTML in JavaScript: A Comparison

- In a standard JavaScript file, this syntax is not valid:

  Attempting to return HTML tags directly will result in an error. This is because JavaScript on its own doesn't understand HTML syntax inside its code.

  ```javascript
  function MyComponent() {
    return <div>Hello World</div>; // This will throw a syntax error in plain JavaScript
  }
  ```

- In React with JSX:

  However, in a React component file (`.js` or `.jsx`), this syntax is perfectly valid, thanks to JSX:

  ```jsx
  function MyComponent() {
    return <div>Hello World</div>; // This will work fine in React
  }
  ```

### Dynamic Binding in JSX

`JSX` supports dynamic content through the use of curly braces `{}`. This allows you to embed JavaScript expressions, including variable values, inside your `JSX` code.

```jsx
function MyComponent() {
  const name = "John";
  return <div>Hello {name}</div>;
}
```

In the above example, the variable `name` is evaluated at runtime and replaced with the value of the variable.

### Differences Between JSX and HTML

While `JSX` closely resembles `HTML`, there are important differences to keep in mind:

1. **Closing Tags:** JSX requires all tags to be closed.

```jsx
// Correct in JSX
<img src="image.jpg" />

// Incorrect in JSX (and HTML)
<img src="image.jpg">

```

2. **Attribute Naming:** JSX uses camelCase for attribute naming.

```jsx
// In HTML
<button onclick="handleClick">Click Me</button>

// In JSX
<button onClick={handleClick}>Click Me</button>
```

3. **className Instead of class:** In JSX, `className` is used instead of the `class` attribute in HTML.

```jsx
// In HTML
<div class="menu" ></div>
// In JSX
<div className="menu"></div>
```

4. **Inline Style Syntax:** In JSX, inline styles are defined as an object with camelCased properties.

```jsx
// HTML
<div style="background-color: blue; font-size: 12px;">Hello</div>

// JSX
<div style={{ backgroundColor: 'blue', fontSize: '12px' }}>Hello</div>

```

5. **JavaScript Expressions:** JSX allows embedding expressions, while JavaScript statements like if-else need to be used outside JSX or rewritten as ternary expressions.

```jsx
// JSX
<h1>{isLoggedIn ? "Welcome back!" : "Please log in"}</h1>

// In traditional HTML, this logic would have to be handled externally with JavaScript.
```

### JSX Compilation with Babel

React uses Babel to convert JSX into a format that browsers can understand. `Babel` transforms JSX into `React.createElement()` calls.

Before Babel Transformation:

```jsx
function MyComponent() {
  return <div>Hello World</div>;
}
```

After Babel Transformation:

```jsx
function MyComponent() {
  return React.createElement("div", null, "Hello World");
}
```

### Conclusion

`JSX` is a powerful and fundamental aspect of React, enabling developers to write readable and maintainable code by seamlessly integrating `JavaScript` and `HTML`. Understanding JSX, its differences from HTML, and how it's transformed for browser compatibility is essential for any developer working with React.
