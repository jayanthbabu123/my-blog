+++
title = 'Authentication in React'
date = 2024-04-13T22:25:55+05:30
draft = false
+++

## Step 1: Store Token and Set Authentication Status

In your React application, after a user logs in successfully, you will receive an authentication token from your backend. This token should be stored in the browser's local storage and used to manage user authentication status across the application. Using React's Context API is an efficient way to share the user's authentication status (whether they are logged in or not) and the authentication token across all components in your application.

To manage authentication status globally, we'll use React's Context API. We'll create a context that contains both the user's authentication status and the token, and provide functions to update these values. This will allow any component in our application to access and modify the user's authenticated state and token.

Here’s how you can set up and use the UserContext:

1. **Create the Context:** Define a new context that will hold the user's authentication status and token.

2. **UserProvider Component:** This component will provide the authentication state to other components. It uses a React state hook to store the user's authentication status and token.

3. **useAuth Custom Hook:** This is a custom hook for accessing the authentication context conveniently from any component.

Here’s how you implement these:

```jsx
// src/UserContext.js
import { createContext, useState, useContext } from "react";

const UserContext = createContext(null);

export const UserProvider = ({ children }) => {
  const [auth, setAuth] = useState({ token: null, isAuthenticated: false });

  return (
    <UserContext.Provider value={{ auth, setAuth }}>
      {children}
    </UserContext.Provider>
  );
};

export const useAuth = () => useContext(UserContext);

export default UserContext;
```

Once the user logs in successfully, you should update the authentication context and local storage. Here's how to adjust your login component to manage this process:

1. Storing the Token: When the login is successful, store the token in local storage to keep the user logged in even if the page is refreshed.

2. Updating Context: Set the isAuthenticated flag and save the token in the context. This allows other components to react to changes in authentication status.

3. Redirecting User: After setting the authentication context, redirect the user to another page, typically a dashboard or home page, using React Router's navigate function.

Here’s the modified login component implementation:

```jsx
// src/Pages/Login/Login.js
import React, { useState } from 'react';
import { useNavigate } from 'react-router-dom';
import axios from 'axios';
import { useAuth } from '../../UserContext';

function Login() {
  const [loginData, setLoginData] = useState({ email: '', password: '' });
  const [errorMessage, setErrorMessage] = useState('');
  const navigate = useNavigate();
  const { setAuth } = useAuth();

  const handleInputChange = (event) => {
    const { name, value } = event.target;
    setLoginData({ ...loginData, [name]: value });
  };

  const handleSubmit = (event) => {
    event.preventDefault();
    axios.post(`http://localhost:5000/api/users/login`, loginData)
      .then((response) => {
        localStorage.setItem('authToken', response.data.token);
        setAuth({ token: response.data.token, isAuthenticated: true });
        navigate('/dashboard');
      })
      .catch((error) => {
        const message = error.response ? error.response.data.message : error.message;
        setErrorMessage(message);
      });
  };

  return (
    // JSX for the form, including event handlers and error messages
  );
}

export default Login;

```

## Step 2: Create a PrivateRoute Component

Creating a PrivateRoute component is a crucial step in protecting certain routes in your React application that should only be accessible to authenticated users. This component checks if the user is authenticated and then either allows access to the protected component or redirects them to a login page if they are not authenticated. Here’s how to implement and use the PrivateRoute component in your application.

Purpose of the PrivateRoute
The PrivateRoute serves as a gatekeeper for any routes that require the user to be authenticated. If the user is not authenticated, they should not be able to access these routes and should instead be directed to log in. This is essential for maintaining the security and integrity of user-specific data that you do not want to expose to unauthenticated users.

Implementation Details
The PrivateRoute uses the React Router v6 API, which introduced significant changes from previous versions. Instead of rendering components directly, we now render an `<Outlet>` that serves as a placeholder for child routes. This is wrapped within a conditional check against the authentication status from our UserContext.

Here's how you can set up the PrivateRoute:

1. Use Context for Authentication Status: First, access the authentication status from the UserContext using the useAuth hook.

2. Conditional Rendering with Navigate: If the user is not authenticated, use the `<Navigate>` component from React Router to redirect the user to the login page.

3. Render Child Components with Outlet: If the user is authenticated, render the `<Outlet>` component that will render the appropriate child components based on the route configuration.

```jsx
// src/components/PrivateRoute.js
import { Navigate, Outlet } from "react-router-dom";
import { useAuth } from "../UserContext";

const PrivateRoute = () => {
  const { auth } = useAuth();

  // Check if the user is authenticated
  if (!auth.isAuthenticated) {
    // Redirect to the login page if not authenticated
    return <Navigate to="/login" />;
  }

  // Render the child routes if authenticated
  return <Outlet />;
};

export default PrivateRoute;
```

**Step 3: Update the App Component to Use PrivateRoute**

Incorporate the PrivateRoute in your application's main routing setup. Wrap any routes that require authentication with the PrivateRoute. In React Router v6, this is achieved by using the PrivateRoute as a parent route and placing protected routes as child elements.

Here’s how you can update the routes in your App component to use PrivateRoute:

```jsx
// src/App.js
import { BrowserRouter, Routes, Route } from "react-router-dom";
import Header from "./Components/Header";
import Dashboard from "./Pages/Dashboard/Dashboard";
import Home from "./Pages/Home/Home";
import Login from "./Pages/Login/Login";
import NotFound from "./Pages/NotFound/NotFound";
import Profile from "./Pages/Profile/Profile";
import SignUp from "./Pages/SignUp/SignUp";
import PrivateRoute from "./components/PrivateRoute";
import { UserProvider } from "./UserContext";

const App = () => {
  return (
    <UserProvider>
      <BrowserRouter>
        <Header />
        <Routes>
          <Route path="/login" element={<Login />} />
          <Route path="/signup" element={<SignUp />} />
          <Route element={<PrivateRoute />}>
            <Route path="/home" element={<Home />} />
            <Route path="/dashboard" element={<Dashboard />} />
            <Route path="/profile" element={<Profile />} />
          </Route>
          <Route path="*" element={<NotFound />} />
        </Routes>
      </BrowserRouter>
    </UserProvider>
  );
};

export default App;
```

In this configuration, the routes `/home`, `/dashboard`, and `/profile` are protected by the PrivateRoute. Users attempting to access these routes without being authenticated will be redirected to the `/login` page.

## Step 4: Update the Header Component

Update the Header component to show/hide links based on authentication status and add a logout button:

```jsx
// src/Components/Header.js
import React from "react";
import { Link } from "react-router-dom";
import { useAuth } from "../UserContext";
import { FontAwesomeIcon } from "@fortawesome/react-fontawesome";
import {
  faDashboard,
  faHouse,
  faUser,
} from "@fortawesome/free-solid-svg-icons";

function Header() {
  const { auth, setAuth } = useAuth();

  const handleLogout = () => {
    localStorage.removeItem("authToken");
    setAuth({ token: null, isAuthenticated: false });
  };

  return (
    <nav className="main-header navbar navbar-expand-lg navbar-light bg-success">
      <div className="container-fluid">
        <div>
          <h4>Trips</h4>
        </div>

        <div className="collapse navbar-collapse" id="navbarNavAltMarkup">
          <div className="navbar-nav">
            {auth.isAuthenticated ? (
              <>
                <div className="nav-link active">
                  <FontAwesomeIcon icon={faHouse} />{" "}
                  <Link to="/home">Home</Link>
                </div>
                <div className="nav-link">
                  <FontAwesomeIcon icon={faDashboard} />{" "}
                  <Link to="/dashboard">Dashboard</Link>
                </div>
                <div className="nav-link">
                  <FontAwesomeIcon icon={faUser} />{" "}
                  <Link to="/profile">Profile</Link>
                </div>
                <div className="nav-link">
                  <button onClick={handleLogout}>Logout</button>
                </div>
              </>
            ) : (
              <>
                <div className="nav-link">
                  <Link to="/signup">SignUp</Link>
                </div>
                <div className="nav-link">
                  <Link to="/login">Login</Link>
                </div>
              </>
            )}
          </div>
        </div>
      </div>
    </nav>
  );
}

export default Header;
```

In this configuration, the routes `/home`, `/dashboard`, and `/profile` are protected by the `PrivateRoute`. Users attempting to access these routes without being authenticated will be redirected to the `/login` page.

This setup ensures that sensitive routes in your application are protected and only accessible to authenticated users, providing a secure and user-friendly navigation experience.


 