+++
title = 'Introduction to React JS - Lession 1'
date = 2024-04-20T13:50:59+05:30
draft = false
weight = 1
tags = [
  "ReactJS",
  "Frontend Development",
  "Modern Web Development",
  "React Development",
  "React Tutorial",
  "ReactJS Tutorial",
  "ReactJS Guide",
  "ReactJS Tips",
  "ReactJS Best Practices",
  "ReactJS Examples",
  "ReactJS Projects",
  "ReactJS Components",
  "ReactJS State Management",
  "ReactJS Hooks",
  "ReactJS Performance",
  "ReactJS Optimization",
  "ReactJS SEO",
  "ReactJS Accessibility",
  "ReactJS Testing",
  "ReactJS Deployment"
]
+++

## 1. What Is React JS?

React JS is a JavaScript library widely adopted for building dynamic user interfaces. It was developed by Facebook and is distinguished by its efficient, declarative, and flexible approach to constructing web application front-ends. Unlike full-fledged frameworks, React focuses exclusively on the UI layer, allowing developers to create highly responsive and interactive web applications.

## Origin and Evolution

The story of React begins with Jordan Walke, a software engineer at Facebook, who created it to address the challenges associated with building dynamic UIs with seamless data updates. React was first deployed on Facebook's newsfeed in 2011 and later released as open source in May 2013. This move allowed it to rapidly gain traction within the development community, benefiting from contributions that spurred its evolution and broad adoption.

## Core Principles of React

1. Components:
   At its core, React operates on the principle of components. These are self-contained modules that encapsulate behavior and rendering logic. Components manage their own state and compose together to form complex UIs. Each component returns a piece of JSX, a syntax that resembles HTML but is powered by JavaScript.

2. JSX:
   JSX is a React extension that makes it easy to write UI components. Its syntax is familiar for anyone who knows HTML, yet it fully utilizes the capabilities of JavaScript. JSX compiles into JavaScript, calling React’s API to render the components into the DOM. This blending of markup with logic seamlessly integrates the development flow.

3. Virtual DOM:
   One of React's most innovative features is the Virtual DOM. This is an in-memory reconstruction of the actual DOM. React creates a tree of custom objects representing the DOM called the Virtual DOM. When a component’s state changes, instead of updating the DOM directly, React updates the Virtual DOM. The library then uses efficient diffing algorithms to calculate the minimal set of changes required to update the real DOM, minimizing performance costs and optimizing updates.

Why Use React?
The adoption of React brings several benefits:

**Efficiency:** React minimizes direct DOM manipulation, which is costly in terms of performance. By using the Virtual DOM, React ensures that the real DOM receives only the necessary changes, leading to faster updates.

**Modularity:** With components, the UI is broken down into individual, manageable pieces that can be developed, maintained, and tested independently.

**Community and Ecosystem:** React’s popularity has led to the creation of a vast ecosystem of tools, extensions, libraries, and frameworks (like Next.js and Gatsby), making it a versatile choice for any web development project.

**Industry Adoption:** Major tech companies like Facebook, Instagram, and Twitter rely on React for its robust features that handle dynamic data efficiently.

## 2. Binding HTML to the DOM with JavaScript and React

Understanding how to add HTML content dynamically to a webpage is a foundational skill in web development. This lesson demonstrates how to do this using both plain JavaScript and React (with its latest version, React 18), showcasing the differences and benefits of each approach.

## Dynamic HTML Binding with JavaScript

First, let's look at how to manually update the DOM using plain JavaScript. This approach involves directly manipulating the web page's content by accessing and modifying the DOM elements.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Plain JavaScript DOM Example</title>
  </head>
  <body>
    <div id="root"></div>
    <script>
      // Using plain JavaScript to add HTML content to the DOM
      document.getElementById("root").innerHTML = "<h1>Hello, World!</h1>";
    </script>
  </body>
</html>
```

In this example, we use JavaScript to find an HTML element by its ID (root) and then set its innerHTML to include an `<h1>` element containing the text `Hello, World!` tag. This method is straightforward but can be inefficient for larger applications or frequent updates because it requires manually managing updates to the DOM.

## Dynamic HTML Binding with React

Next, let's look at how to update the DOM using React. This approach involves creating a React component that renders the HTML content and managing the state of the component.

React simplifies the process of updating the DOM using a declarative approach, where you describe the UI state, and React ensures the DOM matches this state. This example uses React 18, the latest version, to demonstrate binding HTML using JSX, which is a syntax that looks like HTML but lets you include JavaScript.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>React 18 DOM Example</title>
  </head>
  <body>
    <div id="root"></div>
    <script src="https://unpkg.com/react@18/umd/react.production.min.js"></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.production.min.js"></script>
    <script type="text/javascript">
      // Creating a root container using the createRoot method from ReactDOM
      const container = document.getElementById("root");
      const root = ReactDOM.createRoot(container); // Using createRoot for React 18

      // Define what we want to render
      const element = <h1>Hello, World!</h1>; // Using JSX to define HTML elements

      // Render the element using the root instance
      root.render(element);
    </script>
  </body>
</html>
```

In this React setup:

- We use CDN links to include React and ReactDOM libraries directly in the HTML, which simplifies setup without needing a build system or local installation.
- The createRoot method from ReactDOM is utilized to create a root instance tied to the DOM element with the ID root.
- The root.render method is used to render the JSX element into the DOM. This method replaces the older ReactDOM.render and is optimized for concurrent features in React 18.

These examples illustrate two approaches to adding HTML to the DOM. While the JavaScript method provides direct control, it can become cumbersome as applications grow. React's declarative approach, using JSX and efficient DOM updating strategies, not only simplifies the development process but also enhances performance, making it a superior choice for complex applications.

## 3. Understanding React and ReactDOM

React JS fundamentally consists of two main JavaScript libraries: React and ReactDOM. These libraries are crucial in how developers build and manage interactive user interfaces efficiently. Let’s break down their roles and see how they interact with the global window object in the browser.

**React and ReactDOM Libraries**

React is the core library that deals with creating and managing the state of UI components. It allows developers to define components as reusable and isolated pieces of code which can maintain their own state. This modularity enables the creation of complex user interfaces while maintaining clean and manageable code.

ReactDOM complements React by enabling the rendering of components to the DOM, which is necessary for the components to be visible on the web page. It also handles updating the DOM when the state of components changes. This separation of concerns simplifies the development process, making it easier to focus on the UI logic without worrying about the low-level DOM manipulation tasks.

**Interaction with the Window Global Object**

When you include React and ReactDOM in your project, they add properties to the window global object. This is significant because it means you can access React and ReactDOM anywhere in your application without needing to import them in every file. Here’s a basic explanation of how this works:

```js
// In a script that includes React and ReactDOM via CDN links
console.log(window.React); // Outputs the React object
console.log(window.ReactDOM); // Outputs the ReactDOM object
```

Adding these properties to the window object simplifies DOM manipulations in several ways:

**Global Accessibility:** Since React and ReactDOM are attached to the global window object, they can be accessed from any script in the application. This reduces the need for passing React around through imports, making it straightforward especially in simple projects or when you are quickly prototyping.

**Simplified Management of the DOM:** ReactDOM abstracts away the direct interactions with the DOM. Developers can focus on defining the UI logic using React components, and ReactDOM takes care of rendering these components into the DOM and updating them when necessary. This separation makes it easier to develop and maintain complex applications without getting bogged down by the intricacies of the DOM.

**Efficient Updates:** ReactDOM manages the Virtual DOM, which is an in-memory representation of the real DOM. It optimizes updates by only changing elements in the actual DOM that have changed in the Virtual DOM. This results in significantly faster re-renders than traditional DOM manipulation methods.

Understanding that React JS comprises just two main libraries, React and ReactDOM, which manage the UI logic and DOM rendering respectively, clarifies their roles in web development. Their integration into the window global object simplifies their usage across the entire application, fostering more efficient and less error-prone development of dynamic web applications. By abstracting direct DOM interactions, React and ReactDOM allow developers to focus more on designing responsive and intuitive user interfaces.

## 4. Setting Up a Real React Project

Setting up a real React project can seem daunting at first, but it's straightforward once you understand the tools and workflows involved. Below, we explore different ways to create a React project, focusing on methods suitable for beginners and moving to more advanced setups.

## 4.1 Using Create React App

Create React App is a comfortable starting point for beginners. Despite being officially deprecated, its simplicity makes it an excellent tool for learning React without the complexity of configuration.

How to set up with Create React App:

```bash
npx create-react-app my-app
cd my-app
npm start

```

### Understanding of the Folder Structure

When you create a React application using create-react-app, it generates a project with a specific structure that organizes files and directories in a logical and functional manner. Here's a detailed look at the key components:

```bash
my-app
├── node_modules
├── public
│   ├── index.html
│   └── favicon.ico
├── src
│   ├── App.js
│   ├── App.css
│   ├── index.js
│   ├── index.css
│   └── logo.svg
├── package.json
└── README.md

```

`node_modules/`

Contains all the libraries and dependencies your project needs, as specified in package.json. Each dependency is a folder within node_modules.

This folder can become quite large as it includes every library used in your project. It should not be modified directly or committed to version control.

`public/`

- **index.html:** The single HTML file for your entire React application. It typically contains a div element with id="root", where your entire React app is rendered.
- **favicon.ico:** The small icon displayed in the browser tab. You can replace it with your own icon to personalize your app.
- **manifest.json:** A configuration file for Progressive Web Apps (PWA). It defines how your app appears when installed on a user's mobile device or desktop.
- **robots.txt:** Provides instructions to web crawling bots. Useful for SEO optimization.

`src/`

- **App.js:** The main React component that acts as the heart of your application. It's where you'll write most of your application's logic and structure.
- **App.test.js:** The test suite for `App.js`. Use this to test your main component.
- **App.css:** The stylesheet for `App.js`. Use this to style your main component.
- **index.js:** The main entry point of your React app. It defines the structure of your React app and contains the logic to render your app.
- **index.css:** The main stylesheet for your React app. It defines the styling for your app.
- **logo.svg:** The logo displayed in the browser tab. You can replace it with your own logo to personalize your app.
- **reportWebVitals.js:** A JavaScript file that provides a function to measure the performance of your app.

`package-lock.json`: A JSON file that contains information about the dependencies in your project.

`package.json`: A JSON file that contains metadata about your project. It contains information like the name, version, and dependencies.

`README.md`: A Markdown file that provides a description of your project and its purpose.

`.gitignore`: Specifies files and directories that should be ignored by Git. Typically includes `node_modules`, `build artifacts`, etc.

**Exploring Modern Alternatives: Vite and Next.js**

As your React skills grow, you might find that Create React App doesn’t meet all your needs, especially for more complex applications. Modern alternatives like Vite and Next.js offer enhanced performance and additional features out of the box.

## 4.2 Vite:

Vite is a build tool that significantly speeds up the development process by leveraging modern JavaScript features. It serves code via ES modules, making it faster than traditional tools that rely on bundling.

```bash
npm create vite@latest my-vite-app -- --template react
cd my-vite-app
npm install
npm run dev
```

**Advantages:**

- Extremely fast cold server start and hot module replacement (HMR).
- Simple configuration with sensible defaults.
- Optimized build that outputs highly efficient code for production.

## 4.3 Next.js:

Next.js provides a framework for rendering React applications on the server. It's ideal for building scalable applications that benefit from server-side rendering, static site generation, and other modern web technologies.

Setting up a React project with Next.js:

```bash
npx create-next-app my-next-app
cd my-next-app
npm run dev
```

**Advantages:**

- Supports static site generation and server-side rendering out of the box.
- Optimizes performance through automatic code splitting.
- Provides built-in CSS and image optimization.

Choosing the right setup for your React project depends on your specific needs and the scale of the project. For beginners, Create React App provides an easy and comprehensive way to learn React. As you advance, tools like Vite and Next.js offer more control and optimization for larger applications. Each tool has its strengths, and understanding these will help you make the best choice for your project’s requirements.
