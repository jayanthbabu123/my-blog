+++
title = 'Complete guide on Routing in ReactJS - Lession 7'
date = 2024-02-18T12:30:58+05:30
draft = false
+++

# Introduction

Routing is a fundamental aspect of building single-page applications (SPAs) in React.js. React Router version 6 is a popular routing library that allows developers to manage navigation and render different components based on the URL. In this comprehensive guide, we'll cover all the essential concepts of routing in React.js using React Router version 6, providing clear explanations and code examples for each.

## 1. Install React Router

React Router is a powerful routing library for React applications. It allows you to define routes, handle navigation, and render different components based on the URL.

You can install React Router in your project using npm or yarn for that first you need navigate to the project directory and run the following command:

Using npm:

```bash
npm install react-router-dom
```

Using yarn:

```bash
yarn add react-router-dom
```

## Creating Route Components

Before setting up routing in your React application, it's essential to create the components that will be rendered for each route. In this step, we'll create multiple components such as Home, About, and Profile to represent different pages of our application.

**Creating Route Components**

Let's create the components that correspond to different routes in our application:

**Home Component (Home.js):**

```javascript
import React from "react";

function Home() {
  return (
    <div>
      <h1>Welcome to the Home Page!</h1>
      <p>This is the main page of our application.</p>
    </div>
  );
}

export default Home;
```

**About Component (About.js):**

```javascript
import React from "react";

function About() {
  return (
    <div>
      <h1>About Us</h1>
      <p>This is the About Page of our application.</p>
    </div>
  );
}

export default About;
```

**Profile Component (Profile.js):**

```javascript
import React from "react";

function Profile() {
  return (
    <div>
      <h1>Profile Page</h1>
      <p>This is the Profile Page of our application.</p>
    </div>
  );
}

export default Profile;
```

- Each component represents a different page or section of our application.
- The Home component renders the main page content.
- The About component provides information about our company.
- The Profile component displays user profile information.

## Setting Up Routing

Now that we have created the components, it's time to set up routing in our application. Routing typically begins in the main component of your application, often named `App.js`. Here, you integrate React Router to handle navigation and rendering of components based on the URL.

In the example below, we use the `BrowserRouter` component from React Router to establish a routing context for the application. Inside the `BrowserRouter`, we use the Routes component to define individual routes, and each route is represented by the Route component.

```javascript
import React from "react";
import { BrowserRouter, Routes, Route } from "react-router-dom";
import Home from "./components/Home";
import About from "./components/About";
import Profile from "./components/Profile";
import NotFound from "./components/NotFound";

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/profile" element={<Profile />} />
        <Route path="*" element={<NotFound />} />
      </Routes>
    </BrowserRouter>
  );
}

export default App;
```

Now, the routing system is set up to render the appropriate component based on the URL path. For instance:

- Visiting `http://yourdomain.com/` will render the Home component.
- Accessing `http://yourdomain.com/about` will display the About component.
- Navigating to `http://yourdomain.com/profile` will show the Profile component.
- If a user attempts to access a route that doesn't exist, such as `http://yourdomain.com/some-undefined-route`, the `NotFound` component will be rendered.

In React Router, route components play a pivotal role in defining the structure of your application and determining which components to render based on the URL. Let's explore the significance of route components and understand how they contribute to the routing mechanism.

Understanding Route Components
BrowserRouter:

The `<BrowserRouter>` component serves as the root of your routing configuration.
It provides the routing context for the entire application, enabling navigation and rendering of components based on the URL path.
Routes:

The `<Routes>` component is used to define the routes within your application.
It acts as a container for individual `<Route>` components and helps organize the routing structure.
Route:

The `<Route>` component represents a single route in your application.
It specifies the path at which the component should be rendered and the corresponding element to render.

## 4. Navigating Between Routes in React Router

In React Router DOM version 6, navigating between routes is essential for creating dynamic and interactive web applications. There are multiple methods available to achieve navigation within your application, each serving specific purposes. Let's explore how to navigate between routes directly within components, such as from the Home component to the Profile component, and then from the Profile component to the About component.

1. Using `<Link>`:

The `<Link>` component provided by React Router enables users to navigate between different routes by generating clickable links. It updates the URL without causing a full page reload, providing a smooth and seamless navigation experience.

**Home Component (Home.js):**

```javascript
import React from "react";
import { Link } from "react-router-dom";

function Home() {
  return (
    <div>
      <h1>Welcome to the Home Page!</h1>
      <Link to="/profile">Go to Profile</Link>
    </div>
  );
}

export default Home;
```

**Profile Component (Profile.js):**

```javascript
import React from "react";
import { Link } from "react-router-dom";

function Profile() {
  return (
    <div>
      <h1>Profile Page</h1>
      <Link to="/about">Go to About</Link>
    </div>
  );
}

export default Profile;
```

**About Component (About.js):**

```javascript
import React from "react";
import { Link } from "react-router-dom";

function About() {
  return (
    <div>
      <h1>About Page</h1>
      <Link to="/">Go to Home</Link>
    </div>
  );
}

export default About;
```

2. Programmatic Navigation

Programmatic navigation involves navigating between routes programmatically, typically based on user interactions or certain application events. React Router DOM version 6 provides hooks such as `useNavigate` to facilitate programmatic navigation.

```javascript
import React from "react";
import { useNavigate } from "react-router-dom";

function Profile() {
  const navigate = useNavigate();

  function handleNavigateToAbout() {
    navigate("/about");
  }

  return (
    <div>
      <h1>User Profile Page</h1>
      <button onClick={handleNavigateToAbout}>Go to About</button>
    </div>
  );
}

export default Profile;
```

In the Profile component, clicking the button triggers the `handleNavigateToAbout` function, which uses the navigate function from `useNavigate` to navigate to the `"/about"` route programmatically.

## 5. Route Parameters in React Router (Using React Router DOM v6)

Route parameters in React Router allow you to create dynamic routes where certain parts of the URL can change. This feature is particularly useful for handling scenarios where components need to react to specific data or identifiers provided in the URL. Let's explore how to configure parameter routes and how to use these routes in the Home component, including accessing the parameters within the component.

**Configuring Parameter Routes**
To configure parameter routes in React Router DOM version 6, you can define dynamic segments in the URL path using the colon : followed by the parameter name. For example, a parameter route for user profiles might look like this:

```javascript
<Route path="/user/:userId" element={<UserProfile />} />
```

In the example, the `:userId` is a dynamic segment that allows you to access the user ID from the URL. The `UserProfile` component will be rendered based on the user ID provided in the URL.

**Using Parameter Routes in the Home Component**

Let's consider a scenario where the Home component contains a list of users, and clicking on each user should navigate to their respective profile page.

```jsx
import React from "react";
import { Link } from "react-router-dom";

function Home() {
  const users = [
    { id: 1, name: "John" },
    { id: 2, name: "Jane" },
    { id: 3, name: "Doe" },
  ];

  return (
    <div>
      <h1>Welcome to the Home Page!</h1>
      <ul>
        {users.map((user) => (
          <li key={user.id}>
            <Link to={`/user/${user.id}`}>{user.name}</Link>
          </li>
        ))}
      </ul>
    </div>
  );
}

export default Home;
```

In the Home component, we map through a list of users and generate a `<Link>` for each user. The to attribute of the `<Link>` dynamically includes the user's ID in the URL, creating a parameter route to their profile page.

**Accessing Route Parameters Within a Component**

To access route parameters within a component, you can use the useParams hook provided by React Router DOM.

```javascript
import React from "react";
import { useParams } from "react-router-dom";

function UserProfile() {
  const { userId } = useParams();

  return (
    <div>
      <h1>User Profile Page</h1>
      <p>User ID: {userId}</p>
    </div>
  );
}

export default UserProfile;
```

In the `UserProfile` component, the useParams hook allows us to access the route parameters defined in the URL. We can then use userId within the component to fetch user-specific data or perform other actions based on the ID.

## Useful Routing Hooks in React Router DOM

In addition to useParams, React Router DOM version 6 provides several other useful routing hooks that enable developers to access and manipulate routing-related information within their components. Let's explore some of these hooks:

1. useLocation
   The useLocation hook allows you to access the current location object in your component. It provides information about the current URL, including pathname, search, hash, and state.

```javascript
import React from "react";
import { useLocation } from "react-router-dom";

function Home() {
  const location = useLocation();

  return (
    <div>
      <h1>Welcome to the Home Page!</h1>
      <p>Current URL: {location.pathname}</p>
    </div>
  );
}
```

2. useHistory
   The useHistory hook gives you access to the history object, which allows you to programmatically navigate, go back, or go forward in the history stack.

```javascript
import React from "react";
import { useHistory } from "react-router-dom";

function Home() {
  const history = useHistory();

  function goBack() {
    history.goBack();
  }

  function goForward() {
    history.goForward();
  }

  function handleClick() {
    history.push("/profile");
  }

  return <button onClick={handleClick}>Go to Profile</button>;
}
```

3. useMatch

The useMatch hook allows you to check if the current location matches a specified URL or pattern. It's useful for conditional rendering or styling based on the current route.

```javascript
import React from "react";
import { useMatch } from "react-router-dom";

function MyComponent() {
  const isMatch = useMatch("/about");

  return <div>{isMatch ? <h1>About Page</h1> : <h1>Other Page</h1>}</div>;
}
```

These routing hooks provided by React Router DOM version 6 offer powerful capabilities for managing routing and navigation within your React applications. Whether you need to access location information, navigate programmatically, or conditionally render components based on the current route, these hooks provide the necessary functionality to build dynamic and interactive user experiences.

## Conclusion

In this guide, we've explored various aspects of routing in React applications using React Router DOM version 6. Let's summarize the key points:

Basic Usage of React Router: We learned how to set up routing in React applications using components like `<BrowserRouter>`, `<Routes>`, and `<Route>`. By defining routes, we can render different components based on the URL path.

Navigating Between Routes: We explored different methods for navigation, including `<Link>` and `<NavLink>` components for creating clickable links, as well as programmatic navigation using hooks like useHistory and useNavigate. These techniques enable seamless navigation within the application, enhancing the user experience.

Route Parameters: We learned how to configure parameter routes by defining dynamic segments in the URL path. Using the useParams hook, we can access route parameters within components, allowing for dynamic content rendering based on the URL parameters.

Other Useful Routing Hooks: We discovered additional routing hooks like useLocation for accessing current location information, useMatch for conditional rendering based on route matching, and useHistory for programmatically managing the navigation history stack.

In conclusion, React Router DOM version 6 provides a powerful and flexible solution for managing routing and navigation in React applications. By understanding the concepts and utilizing the various features and hooks provided by React Router, developers can create dynamic, interactive, and user-friendly web applications that adapt to different URL paths and user interactions. With the knowledge gained from this guide, you're well-equipped to build robust routing systems and deliver exceptional user experiences in your React projects.


