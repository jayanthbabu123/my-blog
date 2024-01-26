+++
title = 'How I have used Styled Components in React'
date = 2023-12-07T18:12:07+05:30
draft = false
tags = [
  "React",
  "Styled Components",
  "CSS-in-JS",
  "Web Development",
  "Frontend Design",
  "Component Styling",
  "JavaScript",
  "React Library",
  "UI Design",
  "Responsive Design"
]
weight = 15
categories= ["React"]
image= "/images/styled-components-react.png"
+++
![How I have used Styled Components in React](/images/styled-components-react.png)
Styled components have become an essential tool for front-end developers working with React. They allow for the creation of reusable, styled UI components that are encapsulated and easy to maintain. If you’re new to styled components or looking to master them, this comprehensive guide is for you.

From the basics of installation and setup to advanced techniques and best practices, this guide will provide you with everything you need to become a proficient user of styled components in React. Keep reading to learn how to leverage the power of styled components to create beautiful and modular user interfaces.

### Understanding Styled Components 💡

First things first, what are styled-components? In the simplest terms, styled-components is a library for React and React Native that allows you to use component-level styles in your application that are written with a mixture of JavaScript and CSS using a technique called CSS-in-JS.

Styled-components leverage a feature called tagged template literals, available from ES6 onwards, to create normal React components with the added benefit of attached styles.

### Installation 🎯
To start using styled-components in your React projects, you need to set up your development environment first. Here are the steps you need to follow:

Install styled-components package: Begin by installing the styled-components package by running the following command in your terminal:

```bash
npm install styled-components
# or
yarn add styled-components
```

This command installs the latest version of styled-components and updates your package.json file.

For a more consistent and bug-free experience across your project, it’s wise to ensure that only one version of styled-components is installed. Package managers like yarn support a special “resolutions” field in your package.json file, which can help enforce this. Here’s an example of how to set it up:

In package.json:

```json
{
  "resolutions": {
    "styled-components": "^5"
  }
}
```

This setup helps avoid issues that can occur when multiple versions of styled-components exist within your project’s dependency tree.

It’s highly recommended (but not required) to also use the Babel plugin. It offers many benefits like more legible class names, server-side rendering compatibility, smaller bundles, and more.

### Getting Started with Styled Components in React 🌟

Once the package is installed, you can import the necessary components in your React application. Add the following code at the top of your component file:

```jsx
import styled from 'styled-components';

```
This line will import the `styled` function which you will use to create styled components.

**Create a styled component:** Now, you can start creating your own styled components. To do this, you can utilize the `styled` function you imported. This example creates two simple components, a wrapper and a title, with some styles attached to it:

```jsx
import React from 'react';
import styled from 'styled-components';

// Create a Title component that'll render an <h1> tag 
const Title = styled.h1`
  font-size: 1.5em;
  text-align: center;
  color: #BF4F74;
`;

// Create a Wrapper component that'll render a <section> 
const Wrapper = styled.section`
  padding: 4em;
  background: papayawhip;
`;

const App = () => {
  return (
    <Wrapper>
      <Title>Hello World!</Title>
    </Wrapper>
  );
};

export default App;  

```

The above code will render the output like this in the UI.
![Styled components in React](/images/styled-component-demo.png)

### Adapting styles based on props 📦

Adapting styles based on props is a powerful feature of styled-components, allowing for more dynamic and context-aware styling. Below is a simplified example showing how you can alter the style of a button component based on props:

```jsx
import React from 'react';
import styled from 'styled-components';

// Define a styled button with dynamic styles based on props
const StyledButton = styled.button`
  background-color: ${props => props.primary ? 'blue' : 'gray'};
  color: ${props => props.primary ? 'white' : 'black'};
  padding: 10px 15px;
  border: none;
  margin-right:10px;
  border-radius: 5px;
  font-size: 1em;
  cursor: pointer;
  transition: background-color 0.3s ease;

  &:hover {
    background-color: ${props => props.primary ? 'darkblue' : 'darkgray'};
  }
`;

const App = () => {
  return (
    <div>
      <StyledButton>Default</StyledButton>
      <StyledButton primary>Primary</StyledButton>
    </div>
  );
};

export default App;

```

The above code display the output like this

![Styled components in React](/images/styled-demo-1.png)

### Extending styles 🚀
Extending styles is a useful feature of styled-components that allows for additional style rules to be applied to a component, building upon the styles defined in an existing styled component. This is particularly handy for maintaining consistency and DRY (Don’t Repeat Yourself) principles in your codebase. Here’s how you can implement this with a simple example:

```jsx
import React from 'react';
import styled from 'styled-components';

// Base button component
const BaseButton = styled.button`
  padding: 0.6em 1em;
  font-size: 1em;
  cursor: pointer;
  background-color: #ffffff;
  color: #333333;
  margin-right:10px;
  border: 2px solid #333333;
  border-radius: 3px;
  transition: all 0.2s ease-in-out;

  &:hover {
    background-color: #333333;
    color: #ffffff;
  }
`;

// A new component that extends the styles of BaseButton with additional styles
const PrimaryButton = styled(BaseButton)`
  background-color: #007bff;
  color: #ffffff;
  border-color: #007bff;

  &:hover {
    background-color: #0056b3;
    border-color: #0056b3;
  }
`;

const App = () => {
  return (
    <div>
      {/* Usage of BaseButton and PrimaryButton components */}
      <BaseButton>Normal Button</BaseButton>
      <PrimaryButton>Primary Button</PrimaryButton>
    </div>
  );
};

export default App;

```

This pattern is beneficial because it allows you to reuse and extend styles, leading to more maintainable code. It ensures style consistency across components, making your UI more predictable and easier to manage, especially in larger applications with complex style rules.

### Coming From CSS 🌱
When transitioning from traditional CSS methodologies to styled-components, developers need to adjust how they apply styles within their components. The shift involves moving from external CSS files and class name bindings to a more integrated approach where styles are directly part of the component. Let’s break down the transition using your Counter component example.

### 🎨 Traditional CSS Approach
First, let’s look at the traditional approach where CSS is defined externally and brought into the component through class names.

**External CSS File (styles.css):**

```css
/* styles.css */
.counter {
  margin: 0;
  padding: 20px;
  border: 1px solid #ccc;
  text-align: center;
}

.paragraph {
  margin: 0 0 10px 0;
  font-size: 2em;
}

.button {
  padding: 10px 15px;
  font-size: 1.5em;
  cursor: pointer;
}

```

**React Component File (Counter.js):**

```jsx
import React, { useState } from 'react';
// Importing the CSS file
import styles from './styles.css'; 

const Counter = () => {
  const [count, setCount] = useState(0);

  const increment = () => setCount(count + 1);
  const decrement = () => setCount(count - 1);

  return (
    <div className={styles.counter}>
      <p className={styles.paragraph}>{count}</p>
      <button className={styles.button} onClick={increment}>+</button>
      <button className={styles.button} onClick={decrement}>-</button>
    </div>
  );
}

export default Counter;

```

### 📚 Styled-Components Approach
Now, we’ll look at the styled-components approach, where styles are integrated directly into the component file.

Single React Component File with Styled Components (Counter.js):

```jsx
import React, { useState } from 'react';
import styled from 'styled-components';

// Defining styled components
const StyledCounter = styled.div`
  margin: 0;
  padding: 20px;
  border: 1px solid #ccc;
  text-align: center;
`;

const Paragraph = styled.p`
  margin: 0 0 10px 0;
  font-size: 2em;
`;

const Button = styled.button`
  padding: 10px 15px;
  font-size: 1.5em;
  cursor: pointer;
`;

// React functional component using styled components
const Counter = () => {
  const [count, setCount] = useState(0);

  const increment = () => setCount(count + 1);
  const decrement = () => setCount(count - 1);

  return (
    <StyledCounter>
      <Paragraph>{count}</Paragraph>
      <Button onClick={increment}>+</Button>
      <Button onClick={decrement}>-</Button>
    </StyledCounter>
  );
}

export default Counter;

```

In the traditional CSS approach, styles are kept in a separate file, and elements in your component are assigned class names that correspond to the classes in the CSS file. This method keeps a clear separation between your styles and your JavaScript logic but requires managing both class names and the potential complexities of global CSS behavior.

In contrast, the styled-components approach integrates styles directly into your JavaScript file, eliminating the need for separate CSS files and class name bindings. Each styled component is actually a React component with styles attached, promoting a more cohesive and maintainable code structure.

### Advanced Usage: Theming in Styled-Components 💻
Theming is a powerful feature in styled-components, allowing for dynamic styling of components based on hierarchical context. This is achieved using the `<ThemeProvider>` component, which injects theme properties into the React context, making them accessible to styled components throughout the component tree.

1. Basic Theming:

   - Styled components can access props.theme within their template literals, allowing for dynamic styling based on provided theme variables.

   - Themes are passed down from the `<ThemeProvider>` component, which wraps the component tree, ensuring all child components have access to the theme context.

   - Components can have default themes to fall back on when they’re not wrapped in a <ThemeProvider>.

```jsx
import React from 'react';
import styled, { ThemeProvider } from 'styled-components';

// Define a styled button with theming support
const Button = styled.button`
  font-size: 1em;
  margin: 1em;
  padding: 0.25em 1em;
  border-radius: 3px;
  color: ${props => props.theme.main};
  border: 2px solid ${props => props.theme.main};
`;

// Set default props (theme) for the Button
Button.defaultProps = {
  theme: {
    main: "#BF4F74" 
    // default color if not wrapped in a ThemeProvider
  }
}

// Define the theme to be used
const theme = {
  main: "mediumseagreen"
   // the color to be used by the ThemeProvider
};

// Functional App component using the styled Button
const App = () => {
  return (
    <div>
      <Button>Normal</Button> {/* Uses default theme */}
      <ThemeProvider theme={theme}>
        <Button>Themed</Button> {/* Uses theme from ThemeProvider */}
      </ThemeProvider>
    </div>
  );
}

export default App;
```

### ⭐Pro Tips and Best Practices 👍
  - It is important to define your styled components outside of the render method, otherwise it will be recreated on every single render pass. Defining a styled component within the render method will thwart caching and drastically slow down rendering speed, and should be avoided.

  - Beware of Over-styling: It’s tempting to style away, but restraint is key. Unnecessary complexity can sneak into your components, making them harder to read and maintain. Prioritize simplicity and clarity.

  - Keep an Eye on Performance: Remember, styled-components shine with dynamic styling, but overuse can strain performance. Be strategic! Utilize them for components that truly benefit from their power, especially those with varying styles.

### Conclusion ❤️
Styled-components offer a powerful styling solution for your React applications, promoting readability, maintainability, and a rich developer experience. By embracing best practices and exploring advanced features, you can build elegant UIs with clean, logical, and reusable code.

Happy coding to all the innovative minds out there! 🚀
