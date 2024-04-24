+++
title = 'Life Cycle Methods in Class Components Lession 13'
date = 2024-02-20T08:21:09+05:30
draft = false
weight = 13
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

Life cycle methods are special methods in React class-based components that allow you to run code at specific points in a component's life cycle. These methods offer hooks for managing setup, updates, and teardown of your components. The life cycle of a class-based component can be divided into three main phases:

1. Mounting
2. Updating
3. Unmounting

Each phase has its unique set of lifecycle methods that React calls during the component's lifecycle.

## Mounting

The Mounting phase is the initial phase in the lifecycle of a React component. It includes the following key lifecycle methods:

1. Constructor
2. render
3. componentDidMount

Let's explore each of these methods with practical examples to understand their usage and benefits.

**1. Constructor**

The constructor method is the initial step in the lifecycle of a React component, invoked even before the component is attached to the DOM. Its primary role is to set up the component's initial state and bind event handlers. This method is crucial for preparing the component for its journey in the application.

```jsx
class WelcomeComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = { welcomeMessage: "Welcome to React!" };
    this.updateMessage = this.updateMessage.bind(this);
  }

  updateMessage() {
    this.setState({ welcomeMessage: "Thank you for using React!" });
  }
}
```

In this example, the constructor initializes the component's state with a welcome message and binds the updateMessage method, ensuring this within updateMessage refers to the component instance.

**2. render**

Following the constructor, the render method takes the stage. It's the only mandatory method in a class component, tasked with describing what the UI should look like. The render method examines the component's current state and props, returning a React element, which is typically structured as JSX. It's important to note that the render method should be pure, meaning it does not modify component state, and it returns the same output each time it's invoked with the same input.

```jsx
class WelcomeComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = { welcomeMessage: "Welcome to React!" };
    this.updateMessage = this.updateMessage.bind(this);
  }

  updateMessage() {
    this.setState({ welcomeMessage: "Thank you for using React!" });
  }

  render() {
    return (
      <div>
        <h1>{this.state.welcomeMessage}</h1>
        <button onClick={this.updateMessage}>Update Message</button>
      </div>
    );
  }
}
```

The simplicity of the render method belies its importance. It is the heart of the component, dictating the content that will be rendered on the screen. In this example, the render method returns a JSX element that renders the welcome message and a button that triggers the updateMessage method when clicked.

**3. componentDidMount**

Once the component is rendered to the DOM for the first time, the componentDidMount method is called. This lifecycle method is the perfect place for initiating API calls, setting up subscriptions, or performing any operations that require the component to be present in the DOM. It's a critical method for components that need to interact with external data sources or perform side effects.

let see how can we make an api call in componentDidMount method to fetch the list of users from an API.

```jsx
class WelcomeComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = { users: [] };
  }

  componentDidMount() {
    fetch("https://jsonplaceholder.typicode.com/users")
      .then((response) => response.json())
      .then((data) => this.setState({ users: data }));
  }

  render() {
    return (
      <div>
        <h1>Users</h1>
        <ul>
          {this.state.users.map((user) => (
            <li key={user.id}>{user.name}</li>
          ))}
        </ul>
      </div>
    );
  }
}
```

In this example, the componentDidMount method fetches a list of users from an API and updates the state with the fetched data. It is important to note that the componentDidMount method is called only once, after the component has been rendered to the DOM. This ensures that the data is fetched only once.

The `constructor`, `render`, and `componentDidMount` methods collectively establish the foundation for a React component's birth and integration into the application's UI. They enable developers to precisely control the component's initialization, its presentation, and its behavior upon entering the DOM, ensuring a smooth and functional user experience.

## Updating Phase

The Updating phase in the lifecycle of a React component occurs when the component's state or props change, leading to a re-render to reflect the updates in the UI. This phase includes several key lifecycle methods that allow developers to hook into the update process and perform actions at different points. These methods include:

1. shouldComponentUpdate
2. render
3. componentDidUpdate

Let's explore each of these methods with practical examples to understand their usage and benefits.

### shouldComponentUpdate

The shouldComponentUpdate lifecycle method provides a powerful way to optimize React component performance. It is invoked just before the rendering process starts, giving you the opportunity to decide whether a component should proceed with the re-rendering or not. This method receives the next props and state as its arguments, allowing you to compare them with the current props and state.

If `shouldComponentUpdate` returns false, React will skip the rendering for this component and its children, effectively ignoring the changes that triggered the update. This means that even if the state or props of the component have been updated, the component will not re-render, thus avoiding potentially expensive rendering operations. It's a crucial optimization point, especially for large and complex components or those that render a significant amount of children.

It's important to use this method judiciously. Returning false from shouldComponentUpdate prevents the component from updating in response to state or prop changes, which can lead to bugs if not handled correctly. The component will remain as is, displaying potentially outdated information even if its state or props suggest otherwise.

## Scenario: Notification Badge Component

Imagine we're building a social media application where a notification badge displays the number of unread messages a user has. The badge is part of a larger component (let's call it NavBar), which re-renders frequently due to other state changes or prop updates unrelated to the unread messages count. To optimize performance and avoid unnecessary re-renders of the NotificationBadge component, we use shouldComponentUpdate.

```jsx
class NotificationBadge extends React.Component {
  shouldComponentUpdate(nextProps) {
    // Only re-render if unreadMessages prop has changed
    if (this.props.unreadMessages !== nextProps.unreadMessages) {
      return true; // Re-render the component
    }
    return false; // Do not re-render the component
  }

  render() {
    return (
      <div className="notification-badge">
        {this.props.unreadMessages > 0 ? this.props.unreadMessages : ""}
      </div>
    );
  }
}
```

Usage in the NavBar Component

```jsx
class NavBar extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      unreadMessages: 0,
      currentTime: new Date(), // Example of another state that changes frequently
    };
  }

  componentDidMount() {
    // Simulate receiving new messages
    setInterval(() => {
      this.setState((prevState) => ({
        unreadMessages: prevState.unreadMessages + 1,
      }));
    }, 10000);

    // Simulate an update that changes frequently but is irrelevant to the NotificationBadge
    setInterval(() => {
      this.setState({ currentTime: new Date() });
    }, 1000);
  }

  render() {
    return (
      <div className="nav-bar">
        <h1>My Social Media App</h1>
        <NotificationBadge unreadMessages={this.state.unreadMessages} />
      </div>
    );
  }
}
```

In this scenario, the NavBar component includes a NotificationBadge that displays the number of unread messages. The NavBar also contains a state for the current time, which updates every second. Although the frequent updates to the current time trigger re-renders of the NavBar, we don't want these updates to cause the NotificationBadge to re-render unless the number of unread messages changes.

By implementing shouldComponentUpdate in the NotificationBadge component, we ensure that it only re-renders when the unreadMessages prop changes. This method checks if the current prop (this.props.unreadMessages) differs from the next prop (nextProps.unreadMessages). If they are different, it returns true, allowing the re-render. If they are the same, it returns false, preventing an unnecessary re-render.

The render Method in the Update Phase
In React, the render method is one of the most important lifecycle methods. It's responsible for describing what the user interface (UI) should look like based on the component's current state and props. During the lifecycle of a component, the render method is called in both the mounting phase (when the component is first created) and the updating phase (when the component's state or props change).

## How render Works During Updates

When a component's state or props change, React automatically determines that the component needs to be re-rendered to reflect those changes in the UI. This triggers the update phase, and the render method is called again.

React Compares Changes: React compares the new return value of the render method with the previous output to determine what exactly has changed in the DOM.

Efficient DOM Updates: Only the changed elements are updated in the DOM, not the entire tree. This makes updates efficient and fast.

**Key Points About render in the Update Phase:**

**Deterministic:** For the same set of state and props, render must return the same output. This predictability helps React optimize re-renders.

**No Side Effects:** The render method should be pure, meaning it does not modify state, perform data fetching, or directly interact with the browser's DOM. It should solely return a description (typically JSX) of the UI based on the current state and props.

**Performance:** Although React optimizes DOM updates, ensuring that render is efficient is crucial. Avoid complex calculations or operations that could slow down the rendering process.

## componentDidUpdate

The componentDidUpdate method is a lifecycle hook in React class components that is called immediately after a component is updated, i.e., after the component's state or props have changed and the re-render is completed. This method is not called after the initial render. It provides a perfect opportunity to perform operations that need the DOM to be updated and visible, such as DOM manipulations, fetching data based on the new state, or performing calculations based on the new DOM state.

**When to Use componentDidUpdate**

componentDidUpdate is ideal for scenarios where you need to interact with the DOM after the component has updated or when you need to make network requests as a response to a change in props or state. However, it's crucial to ensure that any state updates within this method are placed inside a condition to prevent an infinite loop of updates.

**Key Points:**

**DOM Interactions:** Use it for any interactions with the DOM after an update.

**Network Requests:** Perfect for making API calls in response to a change.

**Conditional Updates:** Always wrap state updates or API calls within a conditional statement to compare the current props or state to the previous ones, preventing infinite loops.

## Practical Example: Fetching Data on User ID Update

Let's consider a component that displays user information. This component allows a user ID to be input. Whenever the input user ID changes, it makes an API call to fetch and display the new user's information using the JSONPlaceholder API.

```jsx
class UserInfo extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      userId: '',
      userData: {},
    };
  }

  componentDidUpdate(prevProps, prevState) {
    // Check if userId state has changed
    if (this.state.userId !== prevState.userId) {
      this.fetchUserData();
    }
  }

  fetchUserData() {
    const { userId } = this.state;
    if (!userId) return; // Exit if userId is not set

    fetch(`https://jsonplaceholder.typicode.com/users/${userId}`)
      .then(response => response.json())
      .then(data =>
        this.setState({
          userData: data,
        })
      )
      .catch(error => console.error('Error fetching user data:', error));
  }

  handleUserIdChange = (event) => {
    this.setState({ userId: event.target.value });
  };

  render() {
    const { userData } = this.state;

    return (
      <div>
        <input
          type="number"
          value={this.state.userId}
          onChange={this.handleUserIdChange}
          placeholder="Enter user ID"
        />
        <div>
          {userData && (
            <div>
              <h2>User Information</h2>
              <p>Name: {userData.name}</p>
              <p>Email: {userData.email}</p>
              {/* Display more user data as needed */}
            </div>
          )}
        </div>
      </div>
    );
  }
}
```

**Explanation:**

`State Management:` The component manages userId and userData in its state. The userId is updated based on user input.

`Component Update:` When the userId changes (detected in componentDidUpdate), fetchUserData is called.

`API Call:` fetchUserData makes an API call to fetch user data based on the current userId. It updates userData in the state with the fetched data, triggering a re-render to display the updated information.
Conditional Execution: The API call is wrapped in a condition within componentDidUpdate to ensure it only runs when userId changes, preventing unnecessary API calls.

componentDidUpdate is a powerful lifecycle method for performing actions in response to component updates. By carefully managing state and props and ensuring conditions are used to prevent unnecessary operations, you can efficiently integrate dynamic data fetching and other responsive behaviors into your React components.

## Unmounting Phase

The unmounting phase is the final stage in the lifecycle of a React component. This phase occurs when a component is being removed from the DOM, providing an opportunity to perform cleanup actions before the component is destroyed. React has a built-in method, componentWillUnmount, which is called just before the component is unmounted and destroyed.

**Example: Component with setInterval**

Consider a component that uses setInterval to periodically update its state. This could be a timer, a counter, or any repetitive task that needs to run at specified intervals as long as the component is mounted.

```jsx
class Timer extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0,
    };
  }

  componentDidMount() {
    this.interval = setInterval(() => {
      this.setState({ count: this.state.count + 1 });
    }, 1000);
  }

  componentWillUnmount() {
    clearInterval(this.interval);
  }

  render() {
    return <div>Count: {this.state.count}</div>;
  }
}
```

In this example, the TimerComponent increments a count in its state by one every second. This is achieved by setting up an interval in the componentDidMount method. The setInterval call returns an ID for the interval, which is stored in this.timerID. This ID is used to clear the interval in the componentWillUnmount method.

The Issue with Not Clearing the Interval

If you omit the `componentWillUnmount` method, or forget to include clearInterval(this.timerID) within it, the interval set up in componentDidMount will continue to run even after the component has been unmounted. This behavior leads to several problems:

Memory Leaks: The callback function passed to setInterval keeps running for a component that is no longer part of the DOM. This can cause parts of your application's logic to keep running unnecessarily, consuming resources and potentially leading to memory leaks.

State Updates on Unmounted Component: The interval's callback function attempts to update the component's state after it has been unmounted. React will throw warnings in the console about this, as updating the state of an unmounted component can lead to bugs and inconsistencies in your application's UI.

## Conclusion

Understanding lifecycle methods in React class components is crucial for managing a component's birth, life, and death within your application effectively. These methods provide hooks into key moments of a component's existence, allowing you to control its behavior and ensure resources are managed efficiently.

During the mounting phase, methods like constructor, render, and componentDidMount let you set up your component, render it to the DOM, and perform any initial data fetching or event listening.

In the updating phase, methods such as shouldComponentUpdate, componentDidUpdate, and occasionally getDerivedStateFromProps offer control over how and when a component updates in response to prop or state changes. They allow for performance optimizations and enable you to react to changes post-update, like fetching new data based on updated props.

The unmounting phase is solely represented by componentWillUnmount, which is your opportunity to clean up any ongoing processes like timers or event listeners to prevent memory leaks and ensure a smooth exit for your component.

In summary, lifecycle methods in class components are essential tools for managing a component's integration into the DOM, its updates, and eventual removal. By leveraging these methods, you can ensure your components behave predictably, perform efficiently, and clean up after themselves, leading to robust and maintainable React applications.







