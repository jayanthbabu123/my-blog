+++
title = 'Usereducer Hook in React Js - Lession 17'
date = 2024-03-13T16:46:18+05:30
draft = false
weight = 17
tags = [
  "ReactJS",
  "useReducer",
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

## Introduction to useReducer

useReducer is a built-in React Hook that provides an alternative to useState for managing complex state logic in React applications. It is particularly useful when dealing with state that is more complex than a simple boolean, number, or string, such as objects or arrays. useReducer is often compared to Redux, Recoil, or MobX, but it can be a more straightforward option for managing state within React components without the need for external libraries 234.

## When to Use useReducer Over useState

**Complex State Logic:** If your state involves multiple values or requires complex logic to update, useReducer is a better choice. It allows you to manage state in a more predictable way by using a reducer function, which is similar to how Redux manages state.
**Performance Optimization:** In scenarios where performance is a concern, useReducer can be more efficient than useState because it allows you to batch multiple state updates into a single render, reducing the number of re-renders.
**State Dependencies:** When the next state depends on the previous state, useReducer is a better option because it ensures that the state updates are processed in the order they were dispatched.

## How to Use useReducer

To use useReducer, you first import it from React: 

```jsx
import { useReducer } from "react";
```


The useReducer hook takes two arguments: a reducer function and an initial state. It returns an array with two elements: the current state and a dispatch function. The reducer function is where you define how the state should be updated in response to different actions.

```jsx
const [state, dispatch] = useReducer(reducer, initialState);
```

```jsx
const initialState = { count: 0 };
function reducer(state, action) {
    switch (action.type) {
        case "increment":
            return { count: state.count + 1 };
        case "decrement":
            return { count: state.count - 1 };
        default:
            throw new Error();
    }
}
```

## Example 1: Counter Functionality with useState and useReducer

**Using useState**

When dealing with simple state management, such as incrementing, decrementing, and resetting a counter, useState is a straightforward choice. Here's how you can implement a counter using useState:

```jsx
import React, { useState } from 'react';

function Counter() {
 const [count, setCount] = useState(0);

 return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <button onClick={() => setCount(count - 1)}>Decrement</button>
      <button onClick={() => setCount(0)}>Reset</button>
    </div>
 );
}

```

In this example, useState is used to manage the counter's state. Each button click updates the state directly, causing the component to re-render and display the updated count.

**Using useReducer**

For more complex state logic, useReducer provides a more structured approach. It's particularly useful when you have multiple related state values or when the next state depends on the previous one. Here's how you can implement the same counter functionality using useReducer:

```jsx
import React, { useReducer } from 'react';

const initialState = { count: 0 };

function reducer(state, action) {
 switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    case 'reset':
      return { count: 0 };
    default:
      return state;
 }
}

function Counter() {
 const [state, dispatch] = useReducer(reducer, initialState);

 return (
    <div>
      <p>Count: {state.count}</p>
      <button onClick={() => dispatch({ type: 'increment' })}>Increment</button>
      <button onClick={() => dispatch({ type: 'decrement' })}>Decrement</button>
      <button onClick={() => dispatch({ type: 'reset' })}>Reset</button>
    </div>
 );
}

```

In this useReducer example, the state and the logic to update it are encapsulated within the reducer function. The dispatch function is used to send actions to the reducer, which then updates the state based on the action type. This approach centralizes the state logic, making it easier to manage and understand, especially as the complexity of the state grows.

## Example-2: Adding Items to a Cart: Using useState and useReducer

**Using useState**

When managing a simple list of items in a cart, useState can be a straightforward choice. Here's how you can implement adding items to a cart using useState:

```jsx
import React, { useState } from 'react';

function Cart() {
 const [cart, setCart] = useState([]);

 const addToCart = (item) => {
    setCart([...cart, item]);
 };

 const removeFromCart = (itemId) => {
    setCart(cart.filter(item => item.id !== itemId));
 };

 const clearCart = () => {
    setCart([]);
 };

 return (
    <div>
      <h2>Cart Items:</h2>
      {cart.map(item => (
        <div key={item.id}>
          <p>{item.name} - ${item.price}</p>
          <button onClick={() => addToCart(item)}>Add</button>
          <button onClick={() => removeFromCart(item.id)}>Remove</button>
        </div>
      ))}
      <button onClick={clearCart}>Clear Cart</button>
    </div>
 );
}

```

In this example, useState is used to manage the cart's state. Each function (addToCart, removeFromCart, clearCart) updates the state directly, causing the component to re-render and display the updated cart.

**Using useReducer**

For more complex state logic, such as managing a cart with multiple items, useReducer provides a more structured approach. Here's how you can implement the same functionality using

```jsx
import React, { useReducer } from 'react';

const initialState = { cart: [] };

function cartReducer(state, action) {
 switch (action.type) {
    case 'ADD_TO_CART':
      return { cart: [...state.cart, action.payload] };
    case 'REMOVE_FROM_CART':
      return { cart: state.cart.filter(item => item.id !== action.payload.id) };
    case 'CLEAR_CART':
      return { cart: [] };
    default:
      return state;
 }
}

function Cart() {
 const [state, dispatch] = useReducer(cartReducer, initialState);

 const addToCart = (item) => {
    dispatch({ type: 'ADD_TO_CART', payload: item });
 };

 const removeFromCart = (itemId) => {
    dispatch({ type: 'REMOVE_FROM_CART', payload: { id: itemId } });
 };

 const clearCart = () => {
    dispatch({ type: 'CLEAR_CART' });
 };

 return (
    <div>
      <h2>Cart Items:</h2>
      {state.cart.map(item => (
        <div key={item.id}>
          <p>{item.name} - ${item.price}</p>
          <button onClick={() => removeFromCart(item.id)}>Remove</button>
        </div>
      ))}
      <button onClick={clearCart}>Clear Cart</button>
    </div>
 );
}

```

In this useReducer example, the state and the logic to update it are encapsulated within the reducer function. The dispatch function is used to send actions to the reducer, which then updates the state based on the action type. This approach centralizes the state logic, making it easier to manage and understand, especially as the complexity of the state grows.

## Conclusion
Both useState and useReducer are powerful hooks in React for managing state. useState is suitable for simple state management needs, while useReducer is better suited for more complex state logic, offering a more structured and predictable way to manage state transitions. The choice between useState and useReducer depends on the specific requirements of your application and your personal preference for managing state.










