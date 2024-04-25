+++
title = 'Complete Guide on State in ReactJS: Lesson 7'
date = 2023-12-30T15:17:53+05:30
weight = 7
draft = false
tags = [
    "ReactJS",
    "State Management",
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
image = "https://i.postimg.cc/T35L4sfW/state-in-react.png"
+++

![State in ReactJS](https://i.postimg.cc/T35L4sfW/state-in-react.png)

### Introduction 🌟

State in React is a way to track how data changes over time in your application. It lets you create components that are dynamic and responsive. In functional components, `state` is handled using the `useState` hook, introduced in React 16.8.

### Declaring State in Functional Components 📝

`State` in functional components is handled using the `useState` hook, which is part of React's Hooks API. Here's how to declare state:

1. **Import useState from React:** 🚀

To use state in a functional component, you first import the `useState` hook from React and then declare `state` variables.

```jsx
import React, { useState } from "react";
```

2. **Using useState:** 🧩

useState is a function that returns an array with two elements. The first element is the current state value, and the second element is a function that updates this value.

```jsx
const [message, setMessage] = useState("Hello React!");
```

In this example, `message` is the state variable, and `setMessage` is the function used to update message.

Lets explore the state declaration with different data types and updating them:

### Using `useState` for String State 🔤

To illustrate, consider a `string` state. In the example below, `useState` initializes the `message` state variable with a default value. The `setMessage` function, also provided by `useState`, is used to update this state.

```jsx
import React, { useState } from "react";

function App() {
  const [message, setMessage] = useState("Hello, React!");

  const updateMessage = () => {
    setMessage("Hello, Updated React!");
  };

  return (
    <div>
      <h1>{message}</h1>
      <button onClick={updateMessage}>Update Message</button>
    </div>
  );
}
```

Here, `message` holds the current state, and clicking the button triggers `updateMessage` to set a new state, demonstrating how state can be updated in response to user actions.

### Using `useState` for Number State 🔢

State management is also effective with numerical values. In the next example, we manage a `count` state. Clicking the button `increments` this count, showcasing how numerical state values can change.

```jsx
import React, { useState } from "react";

function App() {
  const [count, setCount] = useState(0);

  const incrementCount = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <h1>{count}</h1>
      <button onClick={incrementCount}>Increment Count</button>
    </div>
  );
}
```

### Using `useState` for Boolean, Null, and Undefined 🔄

`Boolean`, `null`, and `undefined` values in state behave uniquely as they don't render anything visibly. This characteristic is useful for conditional rendering and toggling states.

```jsx
import React, { useState } from "react";

function App() {
  const [isToggled, setIsToggled] = useState(false);

  const toggle = () => {
    setIsToggled(!isToggled);
  };

  return (
    <div>
      <h1>{isToggled ? "ON" : "OFF"}</h1>
      <button onClick={toggle}>Toggle</button>
    </div>
  );
}
```

The `toggle` function inverses the `isToggled` state, showcasing conditional rendering.

### Handling Object State 🧱

`Objects` in state are useful for grouping related data. To update an object in state, you often need to create a new object to ensure React detects the change and updates the component.

```jsx
import React, { useState } from "react";

function App() {
  const [user, setUser] = useState({ name: "John", age: 30 });

  const updateName = () => {
    setUser({ ...user, name: "Jane" });
  };

  return (
    <div>
      <h1>
        {user.name} is {user.age} years old.
      </h1>
      <button onClick={updateName}>Update Name</button>
    </div>
  );
}
```

Updating the user object's properties demonstrates handling more complex state structures.

### Managing Array State 📊

`Arrays` in state can track lists of items. Below, we demonstrate adding items to an `array` state, illustrating state management for collections and lists.

```jsx
import React, { useState } from "react";

function App() {
  const [items, setItems] = useState(["Item 1", "Item 2"]);

  const addItem = () => {
    setItems([...items, "Item " + (items.length + 1)]);
  };

  return (
    <div>
      <ul>
        {items.map((item) => (
          <li key={item}>{item}</li>
        ))}
      </ul>
      <button onClick={addItem}>Add Item</button>
    </div>
  );
}
```

Here, addItem appends a new item to the items `array`, illustrating state management for collections.

### State Management in Class Components 🧑‍🏫

In React, `class components` have a traditional way of handling state that's distinct from the hooks approach in functional components. Understanding state management in `class components` is particularly important for developers working with older React codebases or transitioning to `functional components`. Let’s delve into how state is declared, initialized, and updated in class components.

**Declaring and Initializing State**

In a class component, state is typically initialized in the `constructor`. Here, this.state is set to an initial state object.

```jsx
import React, { Component } from "react";

class App extends Component {
  constructor() {
    super();
    this.state = {
      count: 0,
    };
  }
  render() {
    return (
      <div>
        <h1>{this.state.count}</h1>
      </div>
    );
  }
}
```

In this example, the Counter component has a state variable count initialized to 0.

**Updating State**

In a class component, state can be updated using the setState method. This method takes an object that contains the new state values.

```jsx
import React, { Component } from "react";

class App extends Component {
  constructor() {
    super();
    this.state = {
      count: 0,
    };
  }

  incrementCount = () => {
    this.setState({ count: this.state.count + 1 });
  };

  render() {
    return (
      <div>
        <h1>{this.state.count}</h1>
        <button onClick={this.incrementCount}>Increment</button>
      </div>
    );
  }
}
```

In this snippet, clicking the `Increment` button will call the `incrementCount` method, which increments the `count` value by 1. Note that `setState` will merge the provided object with the current state.

## Real world analogies for state in React

## 1. Scoreboard in a Sports Game:

Imagine a digital scoreboard at a sports event. The current score (state) is displayed and updated throughout the game using controls (setter function). Each time a team scores, the display is updated (re-rendered) to show the new score. This is like using useState to hold and update the score in a React application, triggering UI updates whenever the state changes.

let's look at a simple example of a cricket scorecard implemented as a React functional component using useState. This component will allow you to update the scores of two teams and display them.

```jsx
import React, { useState } from "react";

function CricketScoreCard() {
  const [teamAScore, setTeamAScore] = useState(0);
  const [teamBScore, setTeamBScore] = useState(0);

  return (
    <div>
      <h1>Cricket Scorecard</h1>
      <div>
        <h2>Team A: {teamAScore}</h2>
        <button onClick={() => setTeamAScore(teamAScore + 1)}>Add 1 Run</button>
        <button onClick={() => setTeamAScore(teamAScore + 4)}>
          Hit 4 Runs
        </button>
        <button onClick={() => setTeamAScore(teamAScore + 6)}>
          Hit 6 Runs
        </button>
      </div>
      <div>
        <h2>Team B: {teamBScore}</h2>
        <button onClick={() => setTeamBScore(teamBScore + 1)}>Add 1 Run</button>
        <button onClick={() => setTeamBScore(teamBScore + 4)}>
          Hit 4 Runs
        </button>
        <button onClick={() => setTeamBScore(teamBScore + 6)}>
          Hit 6 Runs
        </button>
      </div>
    </div>
  );
}

export default CricketScoreCard;
```

## 2. Traffic Lights:

Consider the operation of traffic lights at an intersection. The current light (red, yellow, or green) represents the state. The change from one light to another is controlled by a timer (setter function). Each change in the light requires drivers (the UI) to respond accordingly—stop, get ready, or go. This is akin to updating the state in an app, where each change triggers a response or a UI update.

Creating a React functional component to simulate traffic lights using useState can provide a great example of managing state transitions over time. Let’s build a component that cycles through traffic light phases: Red, Yellow, and Green.

```jsx
import React, { useState, useEffect } from "react";

function TrafficLights() {
  const [light, setLight] = useState("red");

  useEffect(() => {
    const timer = setInterval(() => {
      setLight((currentLight) => {
        switch (currentLight) {
          case "red":
            return "green";
          case "green":
            return "yellow";
          case "yellow":
            return "red";
          default:
            return "red";
        }
      });
    }, 3000); // change light every 3 seconds

    return () => clearInterval(timer); // Clean up the interval on component unmount
  }, []);

  return (
    <div style={{ textAlign: "center" }}>
      <h1>Traffic Light Simulation</h1>
      <div
        style={{
          height: "100px",
          width: "100px",
          borderRadius: "50%",
          backgroundColor:
            light === "red" ? "red" : light === "yellow" ? "yellow" : "green",
        }}
      ></div>
    </div>
  );
}

export default TrafficLights;
```

## 3. Notebook Page:

Think of a notebook where you jot down your to-do list. The items on the page represent the state. Each time you add a new task or cross out a completed one, you are effectively updating the state. The act of writing down a new task or crossing one out is similar to calling the setter function in useState to update the list of tasks.

```jsx
import React, { useState } from "react";

function TodoList() {
  const [tasks, setTasks] = useState([]);
  const [newTask, setNewTask] = useState("");

  const handleAddTask = () => {
    if (newTask !== "") {
      setTasks([...tasks, { id: Date.now(), text: newTask, completed: false }]);
      setNewTask("");
    }
  };

  const handleToggleComplete = (taskId) => {
    setTasks(
      tasks.map((task) =>
        task.id === taskId ? { ...task, completed: !task.completed } : task
      )
    );
  };

  const handleDeleteTask = (taskId) => {
    setTasks(tasks.filter((task) => task.id !== taskId));
  };

  return (
    <div>
      <h1>Todo List</h1>
      <input
        type="text"
        value={newTask}
        onChange={(e) => setNewTask(e.target.value)}
        placeholder="Add a new task"
      />
      <button onClick={handleAddTask}>Add Task</button>
      <ul>
        {tasks.map((task) => (
          <li
            key={task.id}
            style={{ textDecoration: task.completed ? "line-through" : "none" }}
          >
            {task.text}
            <button onClick={() => handleToggleComplete(task.id)}>
              Toggle Complete
            </button>
            <button onClick={() => handleDeleteTask(task.id)}>Delete</button>
          </li>
        ))}
      </ul>
    </div>
  );
}

export default TodoList;
```

### Conclusion 🎯

In React, understanding state management is key whether you're working with class or functional components. Class components offer a traditional approach with `this.state` and `this.setState()`, suitable for complex scenarios and legacy code. Functional components, with the `useState` hook, provide a more modern and concise way to handle state, ideal for simpler components and streamlined code. Being adept in both methodologies is invaluable, ensuring flexibility and effectiveness in building dynamic React applications.

Happy Coding!!
