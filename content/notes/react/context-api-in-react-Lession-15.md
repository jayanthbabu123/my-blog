+++
title = 'Context Api in React - Lesson-15'
date = 2024-03-03T23:06:03+05:30
draft = false
weight = 15
tags =  [
  "ReactJS",
  "Context API",
  "React Components",
  "Frontend Development",
  "Web Development",
  "React Hooks",
  "React Props",
  "React State",
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

The Context API in React is a powerful feature that enables you to easily share data across the entire component tree, eliminating the need to pass props down manually at every level. This is particularly useful for themes, user preferences, authentication data, and more. Here's a detailed guide on how to use the Context API in functional components, from creating a context to consuming it and updating the context value dynamically.

The Context API in React solves a common problem known as "prop drilling," where you need to pass props through several layers of components just to get it to where it's needed. This can make your code messy and hard to maintain, especially in large applications. To illustrate how the Context API can help avoid prop drilling, let's consider a scenario with a Home component that contains three nested components: ComponentA, ComponentB, and ComponentC. We want to pass data from Home directly to ComponentC without having to pass it through ComponentA and ComponentB.

## Without Context API: Prop Drilling Issue

Without the Context API, you'd have to pass the props through each component layer, even if some components don't need the props. It looks something like this:

```jsx
// Home component
function Home() {
  const data = "Data I want to pass to ComponentC";

  return <ComponentA data={data} />;
}

// ComponentA
function ComponentA({ data }) {
  return <ComponentB data={data} />;
}

// ComponentB
function ComponentB({ data }) {
  return <ComponentC data={data} />;
}

// ComponentC
function ComponentC({ data }) {
  return <div>{data}</div>;
}
```

In this setup, ComponentA and ComponentB merely pass the data along without using it, leading to unnecessary prop passing, also known as prop drilling.

## With Context API: Solving Prop Drilling

The Context API allows us to pass data directly from Home to ComponentC without involving the intermediate components. Here’s how you can implement this:

**Step 1: Create a Context**

First, create a context. It's a good practice to put your context in a separate file.

```jsx
// DataContext.js
import React from "react";

const DataContext = React.createContext();

export default DataContext;
```

## Step 2: Provide Context

Use the `DataContext.Provider` to wrap your component tree, providing the data to the entire tree. The value passed to value will be accessible to all child components.

```jsx
// Home component
import React from "react";
import ComponentA from "./ComponentA";
import DataContext from "./DataContext";

function Home() {
  const data = "Data I want to pass to ComponentC";

  return (
    <DataContext.Provider value={data}>
      <ComponentA />
    </DataContext.Provider>
  );
}
```

## Step 3: Consume Context

Now, any component inside the `DataContext.Provider` can access the data, including `ComponentC`, without the need to pass it through `ComponentA` and `ComponentB`.

```jsx
// ComponentC.js
import React, { useContext } from "react";
import DataContext from "./DataContext";

function ComponentC() {
  const data = useContext(DataContext);

  return <div>{data}</div>;
}
```

ComponentA and ComponentB no longer need to pass data as props:

```jsx
// ComponentA.js
import React from "react";
import ComponentB from "./ComponentB";

function ComponentA() {
  return <ComponentB />;
}
```

ComponentB no longer needs to pass data as props:

```jsx
// ComponentB.js
import React from "react";
import ComponentC from "./ComponentC";

function ComponentB() {
  return <ComponentC />;
}
```

## Conclusion

By using the Context API, we've successfully avoided prop drilling, making our code cleaner and more maintainable. The Context API provides a straightforward way to share data across the component tree, from a parent component to deeply nested child components, without the hassle of passing props manually at every level. This is especially useful for frequently needed data like themes, user information, or UI states across your application.
