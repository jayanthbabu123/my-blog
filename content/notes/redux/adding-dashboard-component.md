+++
title = 'Enhancing Our App with and without Redux Toolkit: The Dashboard Component'
date = 2024-04-24T21:19:56+05:30
draft = false
weight = 2
+++

## Introduction

In our series on building a complex application, we've already established the basics of Redux Toolkit and its advantages for state management. Now, let's delve into a practical comparison by creating a Dashboard component both with and without Redux Toolkit. This component will display products fetched from an API, feature search functionality, and manage error handling efficiently.

## Building the Dashboard Component Without Redux Toolkit

### Step 1: Setting Up Component State with React Hooks

Without Redux Toolkit, the state management for our Dashboard component relies solely on React's built-in hooks.

```jsx
import React, { useState, useEffect } from "react";
import axios from "axios";

function Dashboard() {
  const [products, setProducts] = useState([]);
  const [error, setError] = useState("");
  const [searchTerm, setSearchTerm] = useState("");

  useEffect(() => {
    axios
      .get("https://api.example.com/products")
      .then((response) => setProducts(response.data))
      .catch(() => setError("Failed to fetch products"));
  }, []);

  const filteredProducts = products.filter((product) =>
    product.name.toLowerCase().includes(searchTerm.toLowerCase())
  );

  return (
    <div>
      <input
        type="text"
        placeholder="Search products..."
        value={searchTerm}
        onChange={(e) => setSearchTerm(e.target.value)}
      />
      {error && <p>{error}</p>}
      {filteredProducts.map((product) => (
        <div key={product.id}>
          <h3>{product.name}</h3>
          <p>{product.description}</p>
        </div>
      ))}
    </div>
  );
}

export default Dashboard;
```

**Benefits and Drawbacks:**

**Benefits:** This approach is straightforward and uses fewer abstractions, which might be easier for new developers to grasp.

**Drawbacks:** As the application scales, managing state within each component becomes cumbersome and error-prone. It lacks centralized state management, making it difficult to maintain state consistency across the application.

## Building the Dashboard Component With Redux Toolkit

## Step 1: Create a Product Slice

We start by defining a product slice that handles all state logic related to fetching, storing, and searching for products.

Creating a "slice" in Redux Toolkit is an essential step for managing a specific portion of the Redux state. In the context of our Dashboard component, we'll create a product slice that handles everything related to product data. Here’s a detailed breakdown of how to set up the product slice and what each part of the slice accomplishes.

The product slice will:

- Manage the state related to the list of products fetched from an API.
- Handle loading states and error messages.
- Enable searching through the product list based on a user-provided search term.

**Using createAsyncThunk for Asynchronous Actions**

createAsyncThunk is a function from Redux Toolkit that simplifies handling asynchronous logic. It abstracts the standard practice of dispatching actions for pending, fulfilled, and rejected states associated with a promise (such as an API request).

```jsx
export const fetchProducts = createAsyncThunk(
  "products/fetchProducts",
  async (_, { rejectWithValue }) => {
    try {
      const response = await axios.get("https://api.example.com/products");
      return response.data;
    } catch (error) {
      return rejectWithValue("Failed to fetch products");
    }
  }
);
```

- **Action Type Prefix:** `'products/fetchProducts'` is used to automatically generate action types for the lifecycle of the async request (e.g., pending, fulfilled, rejected).
- **Thunk API:** The function takes two arguments: the first one can be used to pass parameters to the thunk, which we don't use here `(\_)`, and the second is a thunk API object that allows you to control the flow of the thunk, such as by using rejectWithValue to return a custom error payload.

- **Axios Request:** We use Axios to make the GET request. On success, the promise resolves to the fetched data, and on failure, it uses rejectWithValue to pass a custom error message.

**Creating the Slice with createSlice**

createSlice is a function that automatically generates action creators and action types corresponding to the reducers you define. It encapsulates both the initial state and the behavior changes of your slice.

```jsx
const productSlice = createSlice({
  name: "products",
  initialState: {
    items: [],
    error: null,
    searchTerm: "",
  },
  reducers: {
    setSearchTerm: (state, action) => {
      state.searchTerm = action.payload;
    },
  },
  extraReducers: {
    [fetchProducts.fulfilled]: (state, action) => {
      state.items = action.payload;
    },
    [fetchProducts.rejected]: (state, action) => {
      state.error = action.payload;
    },
  },
});
```

- **Name:** 'products' identifies the slice and is used as the prefix for generated action types.

- **Initial State:** Defines the starting state of the slice. Here, items will store the product list, error will hold any error messages, and searchTerm is used for filtering the list.

- **Reducers:** setSearchTerm is a reducer that updates the state for the search term. This uses Redux Toolkit's Immer integration, which allows you to write simpler mutable logic that gets converted to correct immutable updates.

- **Extra Reducers:** This field listens to other actions not defined in the slice, particularly our asynchronous fetchProducts thunk actions. fetchProducts.fulfilled updates the items when products are successfully fetched, and fetchProducts.rejected sets the error state in case of an API failure.

```jsx
import { createSlice, createAsyncThunk } from "@reduxjs/toolkit";
import axios from "axios";

export const fetchProducts = createAsyncThunk(
  "products/fetchProducts",
  async (_, { rejectWithValue }) => {
    try {
      const response = await axios.get("https://api.example.com/products");
      return response.data;
    } catch (error) {
      return rejectWithValue("Failed to fetch products");
    }
  }
);

const productSlice = createSlice({
  name: "products",
  initialState: {
    items: [],
    error: null,
    searchTerm: "",
  },
  reducers: {
    setSearchTerm: (state, action) => {
      state.searchTerm = action.payload;
    },
  },
  extraReducers: {
    [fetchProducts.fulfilled]: (state, action) => {
      state.items = action.payload;
    },
    [fetchProducts.rejected]: (state, action) => {
      state.error = action.payload;
    },
  },
});

export const { setSearchTerm } = productSlice.actions;
export default productSlice.reducer;
```

## Step 2: Integrate Redux Store and Dispatch Actions in the Component

This step integrates the product slice with the Redux store and uses it within the Dashboard component.

```jsx
import React, { useEffect } from "react";
import { useSelector, useDispatch } from "react-redux";
import { fetchProducts, setSearchTerm } from "./features/products/productSlice";

function Dashboard() {
  const { items, error, searchTerm } = useSelector((state) => state.products);
  const dispatch = useDispatch();

  useEffect(() => {
    dispatch(fetchProducts());
  }, [dispatch]);

  const filteredProducts = items.filter((product) =>
    product.name.toLowerCase().includes(searchTerm.toLowerCase())
  );

  return (
    <div>
      <input
        type="text"
        placeholder="Search products..."
        value={searchTerm}
        onChange={(e) => dispatch(setSearchTerm(e.target.value))}
      />
      {error && <p>{error}</p>}
      {filteredProducts.map((product) => (
        <div key={product.id}>
          <h3>{product.name}</h3>
          <p>{product.description}</p>
        </div>
      ))}
    </div>
  );
}

export default Dashboard;
```

**Benefits of Using Redux Toolkit:**

- **Centralized State Management:** Enhances scalability and maintainability by centralizing the state, making it easier to manage and debug.
- **Reduced Boilerplate:** createAsyncThunk and createSlice significantly reduce the amount of boilerplate code required for action and reducer creation.
- **Consistent Architecture:** Encourages a consistent architectural pattern across the application, improving team collaboration and code quality.

## Conclusion

Using Redux Toolkit for the Dashboard component simplifies handling complex state interactions and asynchronous operations, providing robust mechanisms for state updates and error handling. As our application continues to grow, leveraging Redux Toolkit’s capabilities will be crucial for maintaining efficiency and ensuring scalability. Stay tuned as we further expand our app's functionality in future posts!
