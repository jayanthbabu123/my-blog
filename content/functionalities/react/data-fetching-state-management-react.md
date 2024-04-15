+++
title = 'Data Fetching and State Management in React'
date = 2024-04-15T14:11:12+05:30
draft = false
+++

## Introduction

React applications often need to interact with external data sources like APIs. Fetching data and efficiently managing the state of this data is crucial for keeping your UI responsive and up-to-date. This guide will demonstrate how to fetch data from a REST API using Axios and display it in a React component. We will use JSONPlaceholder, a free online REST API that you can use to fetch fake data for testing and prototyping.

## Step 1: Installing Axios

`Axios` is a popular, promise-based HTTP client that simplifies making HTTP requests from both the browser and `Node.js`. Its straightforward setup and robust set of features make it an excellent choice for any developer looking to handle HTTP requests.

To begin, you need to add Axios to your React project. Open your terminal, navigate to your project directory, and run the following command:

```jsx
npm install axios
```

This command installs Axios and adds it to your project dependencies, making it available to import and use throughout your application.

## Step 2: Fetching Data from a REST API Using Axios in React

This step involves multiple sub-steps to demonstrate how to fetch and display data in a React application effectively. We'll use JSONPlaceholder as our data source to simulate fetching user data.

**2.1: Declaring State for Storing Users Data**

First, we need to set up the state in our component to store the users data we will fetch from the API. We will initialize this state as an empty array, which will be populated with user data once the data fetching is complete.

Here's how you can set up your React component with state initialization:

```jsx
// src/components/UsersList.js
import React, { useState } from "react";

function UsersList() {
  const [users, setUsers] = useState([]); // State to hold the list of users

  return (
    <div>
      <h1>Users List</h1>
      {/* Data will be rendered here */}
    </div>
  );
}

export default UsersList;
```

**2.2: Making an API Call with Axios Inside useEffect**

Next, we use the useEffect hook to fetch data from the API when the component mounts. This is where Axios comes in to make the HTTP GET request.

```jsx
import React, { useState, useEffect } from "react";
import axios from "axios";

function UsersList() {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    axios
      .get("https://jsonplaceholder.typicode.com/users")
      .then((response) => {
        setUsers(response.data); // Update state with fetched users
      })
      .catch((error) => {
        console.error("Error fetching data:", error);
      });
  }, []); // Dependency array is empty to ensure this runs only once

  return (
    <div>
      <h1>Users List</h1>
      {/* Users data will be rendered here */}
    </div>
  );
}

export default UsersList;
```

**UseEffect Hook:** This hook is used for side effects in function components. Fetching data is a side effect, and here, it's performed once the component is mounted, similar to componentDidMount in class components.

**Axios Get Request:** The axios.get function initiates a GET request to the specified URL. Upon a successful request, the response data is stored in the component’s state using the setUsers function.

**Error Handling:** It’s crucial to handle potential errors in data fetching to prevent crashes and inform users of any issues.

**2.3: Binding the Data in JSX to Display It**

Finally, we need to render the fetched data in our component. We do this by mapping over the users state in the JSX part of our component, displaying each user's information.

Here's the complete component, including the rendering logic:

```jsx
import React, { useState, useEffect } from "react";
import axios from "axios";

function UsersList() {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    axios
      .get("https://jsonplaceholder.typicode.com/users")
      .then((response) => {
        setUsers(response.data); // Update state with fetched users
      })
      .catch((error) => {
        console.error("Error fetching data:", error);
      });
  }, []);

  return (
    <div>
      <h1>Users List</h1>
      <ul>
        {users.map((user) => (
          <li key={user.id}>
            {user.name} - {user.email}
          </li>
        ))}
      </ul>
    </div>
  );
}

export default UsersList;
```

In this final step, each user is rendered as a list item `(<li>)`, displaying the user's name and email. This setup ensures that whenever the users state updates, the component re-renders to reflect the latest data.

## Conclusion

In this guide, we've explored how to fetch data from an API using Axios and manage this data within a React component using state and effects. This approach provides a robust foundation for applications that rely on external data. By managing state and side effects properly, developers can ensure their applications are responsive, reliable, and maintainable.

Fetching data and managing it effectively in React helps keep UI components up-to-date with external changes and user interactions, creating a dynamic and engaging user experience.
