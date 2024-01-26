+++
title = 'How to Implement Nested Routing in React?🌐'
date = 2024-01-06T19:07:41+05:30
draft = false
tags = [
   "ReactJS",
  "Nested Routing",
  "React Router",
  "Frontend Development",
  "Web Development",
  "React Components",
  "Routing in React",
  "React Router Dom",
  "Nested Routes",
  "React Router Configuration",
  "React Router Setup",
  "React Router Tutorial",
  "React Router Example",
  "React Router Best Practices",
  "React Router Navigation",
  "React Router Parameters",
  "React Router Redirect",
  "React Router Guards",
  "React Router Lazy Loading"
]
categories = ["React"]
weight = 11
favorite = true
image = "/images/nested-routing.webp"
+++

![How to Implement Nested Routing in React?](/images/nested-routing.webp)

### Introduction 🧩

Nested routing is a crucial concept in modern web development, especially for those working with React. It allows developers to create more complex and intuitive applications by structuring the user interface in a hierarchical manner. Understanding and implementing nested routing in React not only improves the user experience but also enhances the maintainability of the codebase.

Let’s simplify this concept and guide you through implementing it step by step.

### Understanding Nested Routing Through an Example 🚀

Imagine you have a website with the following URL structure:

- Homepage: `www.yoursite.com/`
- Dashboard: `www.yoursite.com/dashboard`
- Profile (inside Dashboard): `www.yoursite.com/dashboard/profile`
- Settings (inside Dashboard): `www.yoursite.com/dashboard/settings`

Here, ‘Profile’ and ‘Settings’ are nested routes within the ‘Dashboard’. They are part of the Dashboard’s domain but have their unique paths and content.

### Step-by-Step Implementation 🛠️

Implementing nested routing in React is a straightforward process, especially with the use of React Router. In this section, we’ll go through each step, providing detailed explanations and complete code snippets to guide you. By the end of this guide, you’ll have a clear understanding of how to implement nested routing in your React applications.

## Step 1: Setting Up Your React Project 🏗️

Firstly, make sure you have a React project set up. If you’re starting from scratch, you can easily set up a new project using Create React App:

```bash
npx create-react-app my-react-app
cd my-react-app

```

## Step 2: Installing React Router 🔗

React Router is the standard library for routing in React. Install the latest version using npm or yarn:

```bash
npm install react-router-dom
          or
yarn add react-router-dom
```

### Step 3: Creating Basic Components 🧩

Let’s create a few basic components that we’ll use for our routes. For this example, we’ll need a `Home`, `Dashboard`, `Profile`, and `Settings` component. Create these as simple functional components:

```jsx
// Home.js
export function Home() {
  return <h2>Home Page</h2>;
}

// Dashboard.js
export function Dashboard() {
  return <h2>Dashboard Page</h2>;
}

// Profile.js
export function Profile() {
  return <h2>Profile Page</h2>;
}

// Settings.js
export function Settings() {
  return <h2>Settings Page</h2>;
}
```

### Step 4: Setting Up Basic Routing in App.js 🗺️

In your `App.js`, import the necessary components and set up basic routing using `BrowserRouter` and `Routes` from `react-router-dom`.

```jsx
import React from "react";
import { BrowserRouter as Router, Routes, Route } from "react-router-dom";
import { Home } from "./Home";
import { Dashboard } from "./Dashboard";
import { Profile } from "./Profile";
import { Settings } from "./Profile";

function App() {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/dashboard" element={<Dashboard />} />
      </Routes>
    </Router>
  );
}

export default App;
```

### Step 5: Implementing Nested Routing 🧭

Now, let’s add nested routing to the Dashboard component. We want `Profile` and `Settings` to be accessible as nested routes within Dashboard.

First, update the `Dashboard` component to include Outlet, which is where the nested routes will be rendered:

```jsx
// Dashboard.js
import React from "react";
import { Outlet, Link } from "react-router-dom";

export function Dashboard() {
  return (
    <div>
      <h2>Dashboard Page</h2>
      <nav>
        <Link to="/dashboard/profile">Profile</Link>
        <Link to="/dashboard/settings">Settings</Link>
      </nav>
      <Outlet /> {/* Nested routes will render here */}
    </div>
  );
}
```

`Outlet` is a component provided by React Router v6 that acts as a placeholder for nested routes. It renders the appropriate child route component based on the current URL. By including Outlet in our Dashboard component, we tell React Router where to display the nested routes (`Profile` and `Settings` in this case).

### Step 6: Defining Nested Routes in App.js 📐

Now, let’s define the nested routes within the Dashboard route in your `App.js`. This hierarchical structure in the route configuration maps directly to the component hierarchy in your application, providing a clear, organized routing setup.

```jsx
import React from "react";
import { BrowserRouter as Router, Routes, Route } from "react-router-dom";
import { Home } from "./Home";
import { Dashboard } from "./Dashboard";
import { Profile } from "./Profile";
import { Settings } from "./Settings";

function App() {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/dashboard" element={<Dashboard />}>
          <Route path="profile" element={<Profile />} />
          <Route path="settings" element={<Settings />} />
        </Route>
      </Routes>
    </Router>
  );
}

export default App;
```

Here The `Dashboard` component becomes the parent route. The `Profile` and `Settings` components are nested routes within Dashboard.

The Link components in the Dashboard allow users to navigate between the nested routes. When a link is clicked, the URL updates, and React Router renders the corresponding component inside the Outlet of the Dashboard.

Check the demo here

<iframe src="https://codesandbox.io/p/sandbox/react-nested-routing-forked-mvzwtm?file=%2Fsrc%2FDashboard.js%3A10%2C60" style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;" title="Nested Routing React"></iframe>

### Conclusion ✅

In summary, nested routing is a powerful feature in React Router that allows you to create more dynamic, organized, and user-friendly web applications. It not only enhances the structure and maintainability of your code but also significantly improves the overall user experience. As you continue to build and evolve your React applications, leveraging nested routing will undoubtedly be a key factor in your development process.

Happy Coding!!! 🚀👨‍💻👩‍💻
