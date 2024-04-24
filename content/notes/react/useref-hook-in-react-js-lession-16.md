+++
title = 'useRef Hook in React Js - Lession 16'
date = 2024-03-13T15:44:34+05:30
draft = false
weight = 16
tags = [
  "ReactJS",
  "useRef",
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
+++

## Introduction to useRef

useRef is a built-in React Hook that allows you to directly access DOM nodes and persist a mutable value across re-renders of a component without causing a re-render itself. This makes it a versatile tool for various use cases, from manipulating the DOM to storing values that need to persist across renders but do not affect the component's output.

## Key Points About useRef

Direct DOM Access: useRef enables you to access and manipulate DOM nodes directly. This is particularly useful when you need to perform operations that are not possible through React's declarative approach, such as focusing an input field or measuring an element's dimensions.

Persisting Values: Unlike state variables, changes to a ref's .current property do not trigger a re-render. This makes useRef ideal for storing values that need to persist across renders but do not affect the component's output.

Lifecycle: The value stored in a ref persists for the full lifetime of the component instance. This is useful for storing values that need to be accessed or modified in response to events or side effects.
Comparison with useState: While useState is used for values that, when changed, should cause the component to re-render, useRef is used for values that should persist across renders without causing a re-render.

## Practical Examples of useRef

1. Focusing an Input Field: useRef can be used to programmatically focus an input field in response to a user action, such as clicking a button.

```jsx
import { useRef } from "react";

function App() {
  const inputRef = useRef(null);

  function handleClick() {
    inputRef.current.focus();
  }

  return (
    <>
      <input ref={inputRef} />
      <button onClick={handleClick}>Focus the input</button>
    </>
  );
}
```

2. Handling a Form with Email and Password in Uncontrolled Components
   This example shows how to use useRef to handle a form with email and password fields in an uncontrolled manner.

```jsx
import React, { useRef } from "react";

function LoginForm() {
  const emailRef = useRef();
  const passwordRef = useRef();

  const handleSubmit = (event) => {
    event.preventDefault();
    const email = emailRef.current.value;
    const password = passwordRef.current.value;
    alert(`Email: ${email}, Password: ${password}`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <label htmlFor="email">Email:</label>
      <input id="email" type="email" ref={emailRef} />
      <label htmlFor="password">Password:</label>
      <input id="password" type="password" ref={passwordRef} />
      <button type="submit">Submit</button>
    </form>
  );
}
```

3. Directly Changing the Content in an Element

This example demonstrates how to use useRef to directly change the content of an element.

```jsx
import React, { useRef, useEffect } from "react";

function App() {
  const contentRef = useRef();
  const handleChange = () => {
    contentRef.current.textContent = "Content changed!";
  };

  return (
    <>
      <div ref={contentRef}>Original Content</div>
      <button onClick={handleChange}>Change Content</button>
    </>
  );
}
```

## Difference Between useState and useRef

Understanding the distinction between useState and useRef is crucial for effectively managing state and references in React applications. Both hooks are designed to preserve data across re-renders, but they serve different purposes and have distinct behaviors.

## Key Differences

**Re-rendering Behavior:** The primary difference between useState and useRef lies in their impact on component re-rendering. When you update the state using useState, it triggers a re-render of the component. This is because useState is designed to manage state that, when changed, should cause the component to re-render to reflect the new state. On the other hand, useRef does not cause a re-render when its value is updated. This makes useRef suitable for values that need to persist across re-renders without affecting the component's output.

**Return Value:** useState returns an array with two elements: the current state value and a function to update it. This pattern allows you to access and modify the state in a controlled manner. In contrast, useRef returns an object with a current property that holds the actual value. This object is mutable and does not cause a re-render when its value changes.

**Mutability:** The current property of useRef is mutable, meaning you can directly assign new values to it. This is different from the state variable returned by useState, which should not be directly mutated. Instead, you should use the updater function provided by useState to change the state. This distinction is crucial for maintaining the immutability of state in React applications.

**Use Cases:** While both hooks can be considered data hooks, useRef has an additional use case: it can be used to gain direct access to React components or DOM elements. This makes `useRef` particularly useful for operations that require direct manipulation of the DOM or for storing references to instances of external libraries or components.

**useState Example: Controlled Component**

This example demonstrates a controlled component where the input field's value is managed by React state. Every keystroke updates the state, causing the component to re-render and reflect the current value of the input field.

```jsx
import React, { useState } from "react";

const AppDemo10 = () => {
  const [value, setValue] = useState("");
  console.log("render");

  const handleInputChange = (e) => {
    setValue(e.target.value);
  };

  return (
    <div className="App">
      <input value={value} onChange={handleInputChange} />
    </div>
  );
};
```

In this example, the useState hook is used to manage the input field's value. The handleInputChange function updates the state with the current value of the input field every time the user types, causing the component to re-render and display the updated value.

**useRef Example: Uncontrolled Component**

```jsx
import React, { useRef, useEffect } from "react";

function App() {
  const contentRef = useRef();
  console.log("re rendering component");
  const handleChange = () => {
    contentRef.current.textContent = "Content changed!";
  };

  return (
    <>
      <div ref={contentRef}>Original Content</div>
      <button onClick={handleChange}>Change Content</button>
    </>
  );
}
```

In this example the useRef hook is used to manage the content of an element. The handleChange function sets the content of the element to "Content changed!" when the button is clicked. But the component will not re render again for upading the Ref.

## Conclusion

Understanding the differences between `useState` and `useRef` is essential for choosing the right tool for different scenarios in React development. `useState` is used for values that, when changed, should cause the component to re-render, making it ideal for managing UI state. `useRef`, on the other hand, is used for values that need to persist across re-renders without causing a re-render, making it suitable for storing references to DOM elements, instances of external libraries, or any mutable value that does not affect the component's output. By utilizing `useRef` and `useState` correctly, you can build interactive and performant applications with React.
