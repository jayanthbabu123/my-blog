+++
title = 'Introduction to Redux and Redux Toolkit'
date = 2024-04-24T17:29:52+05:30
draft = false
weight = 1
+++

## Introduction

Redux is a tool for managing the state of JavaScript applications. It helps you handle the data and settings that your application needs to operate, all in one place. This is particularly useful in larger applications where managing state directly within components can become messy.

## Why Use Redux?

Imagine your app as a busy airport. Planes (data) are constantly arriving and departing (changing state), and it's crucial that everything is coordinated from one central point to avoid confusion and delays. Without Redux, each component in your app might try to manage its own data, like separate air traffic controllers, which can lead to conflicts and errors as your app grows more complex. Redux simplifies this by having one central "air traffic controller" that handles all the data movements.

Here are the 5 more real world analogies of Redux:

**Central Library:**

Think of Redux as a big library in a town where everyone goes to borrow books. Just like the library keeps track of all the books and who has borrowed them, Redux keeps track of all the information in a React app. This way, no matter where you are in the town (or app), you can always find out what's happening.

**Traffic Cop:**

Imagine Redux as a traffic cop at a busy intersection, directing cars (data) where to go. The cop makes sure that cars don't crash into each other and that everyone knows the rules. This is similar to how Redux manages the flow of data in a React app, making sure that every part of the app knows what it should be doing.

**Conductor of a Train:**

Think of Redux as the conductor on a train who checks tickets and tells passengers where to sit. The conductor keeps everything orderly and makes sure everyone is in the right place, much like Redux does in a React app by organizing and updating the app's data.

**Bank Manager:**

Redux can be thought of as a bank manager who oversees all the transactions in the bank. Just like the manager keeps records of all money coming in and going out, Redux keeps track of all changes to the data in a React app. This ensures that everything stays accurate and up-to-date.

**Party Planner:**

Imagine Redux as a party planner organizing a big event. The planner needs to keep track of the guest list, the food, the music, and everything else to make sure the party goes smoothly. In a React app, Redux is like this planner, managing all the different pieces of information so that the app runs smoothly and everything works together well.

## Transition to Redux Toolkit

While Redux is great at managing data, setting it up involves a lot of repetitive coding. To streamline this process, the creators of Redux developed Redux Toolkit. This toolkit reduces the amount of code you need to write by providing tools that automate some of the setup. It's like upgrading from manual tools to power tools in construction, making building quicker and less prone to errors.

## Modules Used in Traditional Redux vs. Redux Toolkit

**Traditional Redux:**

- **redux:** The core library.
- **react-redux:** Connects Redux with React applications.
- **redux-thunk:** Allows Redux to handle asynchronous operations.
- **redux-logger:** Provides logging for Redux state changes.

**Redux Toolkit:**

- **@reduxjs/toolkit:** A modern toolset that includes everything needed for Redux development in a simpler way.
- **react-redux:** Still used to connect Redux with React.

## Core Parts of the Redux Store

**Traditional Redux Components**

- **Action:** Actions are like notifications that tell the store something happened. For example, an action might be "a user logged in."
- **Reducer:** Reducers are like departments in a company that decide what to do based on the action. If the action is "a user logged in," a reducer might update the state to reflect that a user is now logged in.
- **Store:** The store is like the central database where all state is held. It listens for actions and tells reducers to update the state appropriately.
- **Component:** Components are like the employees who need information to do their jobs. They listen to the store and update themselves when the state changes.

**Redux Toolkit Components**

Redux Toolkit simplifies these components:

- **Slice:** This tool automatically handles the action creation and updating part of reducers based on simple objects you define. It's like a smart form that autofills itself.
- **createReducer:** This helps you write reducers in a simpler way, using modern JavaScript features to avoid common mistakes.
- **configureStore:** This sets up your store with good defaults for most apps, which means less setup for you.
- **createAction and createAsyncThunk:** These tools make it easy to create actions and handle complex operations like fetching data.

By using Redux Toolkit, developers can focus more on creating features rather than setting up and maintaining the state management infrastructure, leading to more efficient and enjoyable development experience.

## 1. Install Dependencies

To set up Redux Toolkit in your React project created with Vite, you'll need to install two main packages: @reduxjs/toolkit and react-redux. Each of these plays a crucial role in integrating Redux into your application.

**@reduxjs/toolkit**

Redux Toolkit is the core of modern Redux development. It provides a set of tools that simplify the creation and management of the Redux store, reducers, and actions. It helps reduce the boilerplate code typically associated with setting up Redux in an application. Key features include:

**configureStore:** Simplifies setup with good defaults for middleware and the Redux DevTools Extension.

**createSlice:** Allows you to define a slice of state along with the reducers and actions. It generates action creators and action types for you.

**createAsyncThunk:** Handles asynchronous logic within your Redux logic. It abstracts the process of dispatching actions and handling state changes related to asynchronous requests like fetching data from an API.

**createReducer:** Lets you write reducers with a simpler syntax that abstracts away the complexities of managing immutable state. This is powered by the Immer library, which allows you to write "mutative" logic that gets translated into correct immutable updates.

**react-redux: Connects Redux with React.**

React-Redux is the official React binding for Redux. It allows your React components to interact with the Redux store efficiently. Key functionalities include:

**Provider:** A React component that allows you to set the Redux store at the top of your application’s component tree, making it accessible to any component that needs to access or modify the Redux state.

**useSelector:** A hook that lets you extract data from the Redux store state. It is used for reading state in your component.

**useDispatch:** A hook that gives you access to the Redux store's dispatch method to dispatch actions.

Here is how you can install these dependencies using npm:

```bash
npm install @reduxjs/toolkit react-redux
```

This command adds the necessary packages to your project, enabling you to configure the Redux store and connect it to your React application. By doing so, you set the stage for efficient state management across your app.

## 2. Set Up the Redux Store

Setting up the Redux store in modern Redux applications typically involves using Redux Toolkit's configureStore method, which offers several enhancements over the traditional createStore method from Redux. Here’s a comparison and explanation of how configureStore simplifies and improves the store setup process:

**Traditional createStore**

In traditional Redux setups using `createStore`, you manually configure many aspects of the Redux store:

**Middleware:** You need to explicitly apply middleware like Redux Thunk for handling asynchronous actions or Redux Logger for debugging.

**Reducers:** Combining multiple reducers requires using combineReducers before passing them to createStore.

**DevTools Extension:** Integrating tools like Redux DevTools involves manually setting up enhancers, often requiring additional boilerplate code to ensure they are only included in development builds.

Here’s an example setup using createStore:

```js
import { createStore, combineReducers, applyMiddleware, compose } from "redux";
import thunk from "redux-thunk";
import logger from "redux-logger";
import rootReducer from "./reducers"; // Your combined reducers

const composeEnhancers = window.__REDUX_DEVTOOLS_EXTENSION_COMPOSE__ || compose;
const store = createStore(
  combineReducers(rootReducer),
  composeEnhancers(applyMiddleware(thunk, logger))
);
```

**Using configureStore from Redux Toolkit**

`configureStore` simplifies the setup by automatically configuring the store with good defaults for most applications:

**Middleware:** Redux Toolkit automatically applies redux-thunk and sets up the Redux DevTools Extension. It also includes a serializable state invariant middleware and an immutability middleware in development mode to help catch common mistakes.

**Reducers:** configureStore accepts a reducer parameter that can either be a single reducer function or an object of slice reducers, which it automatically combines for you.
**Enhancements:** It simplifies the integration of the Redux DevTools Extension by enabling it by default with capabilities such as action traceability, state diffing, and time-travel debugging.

Here's how to set up the store using configureStore:

```js
import { configureStore } from "@reduxjs/toolkit";
import counterReducer from "./features/counter/counterSlice"; // Example of a slice reducer

export const store = configureStore({
  reducer: {
    counter: counterReducer,
  },
});
```

**Benefits of configureStore**

**Simplicity:** Reduces boilerplate code and simplifies initial setup, making it more accessible, especially for new developers.

**Safety:** Built-in middleware helps prevent common mistakes such as mutating the state directly or dispatching non-serializable values.
**Performance:** Includes optimizations for development and production builds, such as excluding expensive middleware in production.

By using configureStore, developers gain a more streamlined and error-resistant setup, allowing them to focus on developing features rather than configuring the state management infrastructure. This approach not only improves developer productivity but also enhances the overall maintainability and robustness of the application.

## 3. Creating a Slice

The concept of "slices" in Redux Toolkit represents a more modern approach to structuring reducers and actions compared to traditional Redux. Here's a comparison of the previous approach and the benefits provided by using createSlice.

**Traditional Approach: Manual Reducers and Actions**

In traditional Redux, you need to manually define action types, action creators, and reducers. This process involves multiple steps:

**Action Types:** Define constant identifiers for each action.
**Action Creators:** Write functions that create action objects with a type field and any necessary data.
**Reducers:** Implement reducers that take the current state and an action, and return a new state based on the action type.

Here’s an example of a traditional Redux setup for a counter:

```js
// Action Types
const INCREMENT = "INCREMENT";
const DECREMENT = "DECREMENT";

// Action Creators
function increment() {
  return { type: INCREMENT };
}

function decrement() {
  return { type: DECREMENT };
}

// Reducer
function counterReducer(state = 0, action) {
  switch (action.type) {
    case INCREMENT:
      return state + 1;
    case DECREMENT:
      return state - 1;
    default:
      return state;
  }
}

// Usage
const store = createStore(counterReducer);
```

**Modern Approach: Using createSlice**

createSlice from Redux Toolkit simplifies this entire process by encapsulating reducers and actions into a single coherent configuration. A "slice" contains the logic for a single piece of your state and includes the following:

**Name:** Identifies the slice.

**Initial State:** The initial state for the reducer.

**Reducers:** Functions that handle actions and update the state. Action creators are automatically generated based on these reducers.

Here’s how the same counter example can be implemented using createSlice:

```js
import { createSlice } from "@reduxjs/toolkit";

const counterSlice = createSlice({
  name: "counter",
  initialState: 0,
  reducers: {
    increment: (state) => state + 1,
    decrement: (state) => state - 1,
  },
});

export const { increment, decrement } = counterSlice.actions;
export default counterSlice.reducer;
```

**Benefits of createSlice**

**Reduced Boilerplate:** Automatically generates action types and creators, reducing the need to manually define them.

**Simplified Configuration:** Consolidates the definition of initial state, reducers, and actions into a single function call, making the code easier to read and maintain.

**Immutability Enforcement:** Internally uses Immer to handle state updates, which allows you to write simpler mutable logic that gets converted to correct immutable updates.

**Consistency:** Ensures that all parts of the slice (actions and reducers) are consistently named and linked, reducing common bugs related to mismatches between action types and reducers.

Using `createSlice` not only streamlines the development process by cutting down on repetitive code but also enhances the maintainability of the application by keeping related logic grouped together and reducing the chances of errors.

## 4. Add the Slice Reducer to the Store

In your store.js file, import the reducer from the slice and add it to the reducer field in the `configureStore` method.

```js
// src/store.js
import { configureStore } from "@reduxjs/toolkit";
import counterReducer from "./features/counter/counterSlice";

export const store = configureStore({
  reducer: {
    counter: counterReducer,
  },
});
```

## 5. Provide the Redux Store to Your Application

Wrap your application in a `<Provider>` component from React-Redux and pass the store as a prop. This step typically goes in your main entry file, like `main.jsx` or `App.jsx`.

```jsx
// src/main.jsx
import React from "react";
import ReactDOM from "react-dom";
import { Provider } from "react-redux";
import App from "./App";
import { store } from "./store";

ReactDOM.render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.getElementById("root")
);
```

## 6. Using Redux State and Actions in Your Components

Incorporating Redux Toolkit into a React component fundamentally changes how state management is handled, shifting from local state management to a more centralized approach. Here’s an overview of how components are modified from managing state internally to using Redux Toolkit for state management.

**Before Redux: Local State Management**

Before integrating Redux, a React component might manage state locally using React's useState hook. For example, consider a simple counter component:

```jsx
import React, { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <h1>Count: {count}</h1>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <button onClick={() => setCount(count - 1)}>Decrement</button>
    </div>
  );
}

export default Counter;
```

In this setup, the component is self-contained, with all state logic handled within the component itself. This is simple and works well for small applications, but as complexity grows, managing state locally can lead to duplications and harder-to-maintain code.

**After Redux Toolkit: Centralized State Management**

After integrating Redux Toolkit, the state management is centralized in the Redux store, and components access this state or dispatch actions using hooks provided by react-redux. Below is how you can modify the same counter component to use Redux Toolkit:

1. **Set up the Redux Slice:** As explained earlier, you would define your Redux logic in a slice. Here’s a brief recap of the counter slice setup:

```js
import { createSlice } from "@reduxjs/toolkit";

const counterSlice = createSlice({
  name: "counter",
  initialState: 0,
  reducers: {
    increment: (state) => state + 1,
    decrement: (state) => state - 1,
  },
});

export const { increment, decrement } = counterSlice.actions;
export default counterSlice.reducer;
```

2. **Modify the Component to Use Redux:** Replace local state management with Redux state and dispatch functions. Here's how the Counter component would look:

```jsx
import React from "react";
import { useDispatch, useSelector } from "react-redux";
import { increment, decrement } from "./features/counter/counterSlice";

function Counter() {
  const count = useSelector((state) => state.counter);
  const dispatch = useDispatch();

  return (
    <div>
      <h1>Count: {count}</h1>
      <button onClick={() => dispatch(increment())}>Increment</button>
      <button onClick={() => dispatch(decrement())}>Decrement</button>
    </div>
  );
}
```

**explaination**

- **React** is imported as it is necessary for defining the component and using JSX.
- **useSelector** and **useDispatch** are React-Redux hooks that allow the component to interact with the Redux store. useSelector is used to access the current state, and useDispatch returns a reference to the dispatch function from the Redux store to send actions.

- **increment** and **decrement** are action creators generated by the createSlice function in Redux Toolkit. They are imported from a file where the counter slice is defined, enabling dispatching these actions to update the state.

**The Counter function defines the component.**

- useSelector is used to retrieve the current count value from the Redux store's state. The argument state => state.counter is a selector function that specifies the part of the state to access, in this case, state.counter.
- useDispatch is called to obtain the dispatch function, which is used to send actions to the Redux store to trigger state changes.

- The component returns JSX that renders the UI. It includes a `<div>` element containing an `<h1>` element that displays the current count and two `<button>` elements to change the count.
- The count, displayed inside `{count}`, is dynamically rendered based on the current state in the Redux store.
- Each button has an onClick event handler that dispatches an action when clicked. `dispatch(increment())` is called when the increment button is clicked, sending an increment action to the store, which updates the state by increasing the count. Similarly, `dispatch(decrement())` is called when the decrement button is clicked, which sends a decrement action to decrease the count.

By moving state management out of the components and into the Redux store, components become lighter and more focused on UI logic rather than state handling, making the overall architecture cleaner and more scalable.

## Conclusion

This guide provides you with a basic setup of Redux Toolkit in a Vite-based React project. Depending on your application's complexity and requirements, you might want to expand your Redux setup by adding more slices, using middleware like Redux Thunk for asynchronous actions, or further configuring the store.
