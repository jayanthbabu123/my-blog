+++
title = 'Complete Guide on Props in React: Lesson-8'
date = 2023-12-30T23:55:34+05:30
weight = 8
draft = false
tags = [
    "ReactJS",
    "Props",
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
image = "https://i.postimg.cc/mZ1zPGQc/props-react.png"
+++

![Props in React: A Comprehensive Guide](https://i.postimg.cc/mZ1zPGQc/props-react.png)
### Introduction 🌐

Props, short for "properties," are a fundamental concept in React. They are the mechanism through which data is passed from a parent component to a child component. Props are read-only, meaning they are `immutable`. This immutability is crucial because it helps maintain the integrity and predictability of the UI by ensuring that a component cannot alter its own props.

### Passing Props to a Component: Button Example 👇

To demonstrate how to pass props to a component, let's create a simple component. This component will accept a prop that sets its label.

**Button Component:**

```jsx
function Button(props) {
  return <button>{props.label}</button>;
}
```

In this `Button` component, `props.label` is used to display the text on the button.

Now, let's pass a prop to this `Button` component from a parent component, such as the App component.

**App Component:**

```jsx
import React from "react";
import Button from "./Button"; // Assume Button is in a separate file

function App() {
  return (
    <div>
      <Button label="Click Me" />
      <Button label="Submit" />
      <Button label="Cancel" />
    </div>
  );
}

export default App;
```

Inside the `App` component's render method, we use the `Button` component multiple times, each time passing a different `label` prop.

This setup illustrates how props can be used to pass data to child components and how they enable components to be reusable and dynamic. Each Button instance renders with a different label, showcasing the flexibility that props provide in React components.

### Passing Props with Different Data Types: UserProfile Example 🔄

To demonstrate passing props of various data types, let's create a `UserProfile` component. This component will accept several props including `strings`, `numbers`, and `arrays`.

**UserProfile Component:**

```jsx
function UserProfile(props) {
  return (
    <div>
      <h1>Name: {props.name}</h1> {/* String */}
      <p>Age: {props.age}</p> {/* Number */}
      <p>Email: {props.email || "Not Provided"}</p> {/* String or Undefined */}
      <h3>Hobbies:</h3>
      <ul>
        {props.hobbies.map((hobby, index) => ( {/* Array */}
          <li key={index}>{hobby}</li>
        ))}
      </ul>
    </div>
  );
}

```

In the `UserProfile` component, we handle different types of props:

- name and email are strings.
- age is a number.
- hobbies is an array.

Now let's use the `UserProfile` component in our `App` component and pass it the various props.

**App Component:**

```jsx
import React from "react";
import UserProfile from "./UserProfile";

function App() {
  return (
    <div>
      <UserProfile
        name="John Doe"
        age={30}
        email="john@example.com"
        hobbies={["Cooking", "Reading", "Traveling"]}
      />
    </div>
  );
}

export default App;
```

In the `App` component, We render the `UserProfile` component and pass it different types of props: a `string` for `name` and `email`, a `number` for `age`, and an `array` for `hobbies`.

**UserProfile Component with Object Destructuring** 🔀

`Object destructuring` is a convenient feature in JavaScript that can make your React components cleaner and more readable. Instead of accessing props using `props.name`, `props.email`, etc., you can destructure these properties directly in the function parameters. This approach simplifies the code within your component.

Here's how the `UserProfile` component looks when using object destructuring:

```jsx
function UserProfile({ name, email, age, hobbies }) {
  return (
    <div>
      <h1>Name: {name}</h1>
      <p>Email: {email}</p>
      <p>Age: {age}</p>
      <h3>Hobbies:</h3>
      <ul>
        {hobbies.map((hobby, index) => (
          <li key={index}>{hobby}</li>
        ))}
      </ul>
    </div>
  );
}
```

In this version of the `UserProfile` component, we've destructured `name`, `age`, `email`, and `hobbies` from props right in the function signature. This technique not only makes the component more concise but also enhances its readability.

This example shows how flexible props are in terms of the data types they can represent. By passing different types of props to the `UserProfile` component, we can display a rich set of data in a structured format, demonstrating the power of props in building dynamic and data-driven components in React.

### Setting Default Props in React 📌

`Default props` in React provide a way to define default values for a component's props. This feature is particularly useful when you expect certain props to be optional and want to ensure your component behaves correctly even when those props are not provided.

**Implementing Default Props**

Let's enhance the `UserProfile` component to have default values for its props. This way, if certain props aren't passed, the component will still render with these default values.

**UserProfile Component with Default Props:**

```jsx
function UserProfile({ name, age, email, hobbies }) {
  return (
    <div>
      <h1>Name: {name}</h1>
      <p>Age: {age}</p>
      <p>Email: {email}</p>
      <h3>Hobbies:</h3>
      <ul>
        {hobbies.map((hobby, index) => (
          <li key={index}>{hobby}</li>
        ))}
      </ul>
    </div>
  );
}

UserProfile.defaultProps = {
  name: "Anonymous",
  age: "Not specified",
  email: "No email provided",
  hobbies: ["None"],
};
```

In this version of the `UserProfile` component, we've added default values for `name`, `age`, `email`, and `hobbies` to the `UserProfile` component.

Now, let's use the `UserProfile` component without providing all the props to see how default props work.

**App Component:**

```jsx
import React from "react";
import UserProfile from "./UserProfile";

function App() {
  return (
    <div>
      <UserProfile />
    </div>
  );
}

export default App;
```

In the `App` component, we render the `UserProfile` component without passing any props. This shows that default props are used for the `name`, `age`, `email`, and `hobbies` props.

When rendering `UserProfile` without any `props`, the default values specified in UserProfile.defaultProps will be used.

### Accessing Props in Class-Based Components 👨‍💻

In a class component, props are accessed via the this.props object. This object contains all the props passed to the component and is readily available in any of the component's methods, including the render method.

```jsx
import React from "react";

class Welcome extends React.Component {
  render() {
    // Accessing props using this.props
    const { name, greeting } = this.props;

    return (
      <div>
        <h1>
          {greeting}, {name}!
        </h1>
      </div>
    );
  }
}

// Usage
<Welcome name="John" greeting="Hello" />;
```

In this Welcome component:

- Props are accessed in the render method using `this.props`.
- We destructure the name and greeting props from `this.props` for ease of use.
- The component then uses these props to render a personalized greeting message.

In class-based components, `this.props` is the gateway to accessing props throughout the component. It's a fundamental aspect of class components in React, allowing for dynamic rendering and interaction based on props received from parent components.

### Why Props are Immutable in React

In React, props are immutable. This means once a prop is set by a parent component, it cannot be changed by the child component that receives it. This immutability is a core principle in React's design, emphasizing predictable data flow and component reusability.

**Why are Props Immutable?**

1. **Predictability:** Immutable props ensure that UI components behave like pure functions with respect to their inputs. This predictability makes components easier to understand and debug.
2. **Component Reusability:** When components don’t modify their own props, they can be reused in different contexts without unexpected side effects.
3. **Performance Optimization:** React can optimize re-renders and updates since it can assume that props don’t change.

**What Happens If You Try to Change Props?** 🚫

React components should treat props as read-only. Trying to change props directly within a component will not work as expected and can lead to bugs and unpredictable behavior.

```jsx
function Greeting({ message }) {
  // Trying to modify a prop (incorrect approach)
  message = "Welcome to React!"; // This will cause an error or unexpected behavior

  return <h1>{message}</h1>;
}

// Usage
<Greeting message="Hello, React!" />;
```

In this example, attempting to reassign the message prop inside the `Greeting` component is incorrect. React will either throw an error or ignore this modification, as `props` are read-only.

### Conclusion 🎓

In React, whether you're working with functional or class-based components, understanding `props` is key to creating dynamic and interactive user interfaces. `Props` allow for the passage of data between components, making them essential for component reusability and composition. In functional components, `props` are accessed directly in the component function, while in class components, `this.props` is used. Remembering that props are read-only and should be treated as immutable helps maintain predictable and manageable component behavior.

Happy Coding!!
