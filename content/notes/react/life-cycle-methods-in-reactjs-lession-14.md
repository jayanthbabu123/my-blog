+++
title = 'Life Cycle Methods in Functional Components - Lession 14'
date = 2024-02-18T13:42:42+05:30
draft = false
weight = 14
tags = [
  "ReactJS",
  "Life Cycle Methods",
  "React Components",
  "Frontend Development",
  "Web Development",
  "React Props",
  "React State",
  "React Hooks",
  "React Context",
  "React Redux",
  "React Data Flow",
  "React Event Handling",
  "React Rendering",
  "React Virtual DOM",
  "React Performance",
  "React Best Practices",
]
categories = ["React-Training"]
+++

# Introduction

In functional components, we can use React hooks to replicate the behavior of class-based life cycle methods.
Hooks were introduced in React 16.8 to allow function components to manage state and side effects, similar to class components. The useEffect hook is particularly useful for lifecycle behaviors.

**Phases of the React Component Lifecycle**

A React component undergoes three major phases:

1. Mounting: Occurs when a component is first created and inserted into the DOM. (ComponentDidMount)
2. Updating: Occurs when changes to a component's props or state trigger a re-render. (ComponentDidUpdate)
3. Unmounting: Occurs when a component is removed from the DOM. (ComponentWillUnmount)

## Writing Life Cycle Methods:

In functional components, we can use React hooks to replicate the behavior of class-based life cycle methods. The useEffect hook is particularly useful for defining life cycle behavior in functional components.

Below are the commonly used life cycle methods in functional components along with their equivalents using the useEffect hook:

### Using useEffect in the Mounting Phase

The mounting phase refers to the point when a React component is rendered and inserted into the DOM for the first time. It's an ideal stage for initializing state, fetching data, and setting up subscriptions.

```jsx
import React, { useEffect } from "react";

const App = () => {
  useEffect(() => {
    console.log("Mounting Phase");
  }, []);

  return <div>Hello World</div>
};
```

In this example, the useEffect hook with an empty dependency array [] mimics the componentDidMount lifecycle method. The cleanup function inside the useEffect is not necessary for the mounting phase but is included to demonstrate how you would prepare for component unmounting.

### Using useEffect in the Updating Phase

The updating phase refers to the point when a React component's state or props are changed and the component is re-rendered. It's an ideal stage for updating state or fetching data.

```jsx
import React, { useEffect, useState } from "react";

const App = () => {
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log("Updating Phase");
  }, [count]);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
};
```

In this example, the effect runs whenever the count state changes because count is listed in the dependency array. This setup allows for specific logic to execute in response to state or prop updates.

### Using useEffect in the Unmounting Phase

The unmounting phase refers to the point when a React component is removed from the DOM. It's an ideal stage for cleaning up resources.

```jsx
import React, { useEffect } from "react";

const App = () => {
  useEffect(() => {
    return () => {
      console.log("Unmounting Phase");
    };
  }, []);

  return <div>Hello World</div>
};
```

In this example, the useEffect hook returns a cleanup function that logs a message when the component is unmounted.

## Conclusion

In this lesson, we learned how to use React hooks to replicate the behavior of class-based life cycle methods in functional components. `useEffect` is a powerful hook that can be used to define lifecycle behavior in functional components. It can be used in the mounting, updating, and unmounting phases of the component lifecycle.





