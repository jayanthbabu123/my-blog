+++
title = 'Creating a Toggleable List and Grid View in React'
date = 2024-04-14T22:23:00+05:30
draft = false
+++

This tutorial demonstrates how to build a React application where you can display products in a list or a grid view, with separate buttons to switch between these views. We’ll walk through setting up the project, creating data files, developing a React component, and styling it—all aimed at beginners.

## Step 1: Set Up Your Project

Before starting, make sure you have `Node.js` installed on your computer as it includes `npm` (node package manager) which is essential for managing the libraries that React uses.

**Create a new React application:** Open your terminal or command prompt and run the following commands. This sets up a new project using the `create-react-app` starter kit, which provides a robust and simple setup:

```bash
npx create-react-app my-product-app
cd my-product-app

```

This creates a directory called `my-product-app` with all the necessary files and configurations automatically set up.

## Step 2: Create a Product Data File

Now, let’s simulate a backend by creating a static list of products. This is a common practice for learning and testing without the need for an actual backend server.

1. **Create a folder for your data:** Navigate to the `src` directory of your React app and create a new folder named data. This will help organize your project by separating data from your components.

2. **Add your product data:**

- In the **data** folder, create a file named `products.js`.
- Open `products.js` and input an array of objects where each object represents a product. Here’s how you can structure it:

```js
// src/data/products.js
const products = [
  {
    id: 1,
    name: "Laptop",
    description:
      "High-performance laptop ideal for gaming and software development.",
    price: "$999",
  },
  {
    id: 2,
    name: "Smartphone",
    description:
      "Latest smartphone with high-resolution camera and long-lasting battery.",
    price: "$499",
  },
  {
    id: 3,
    name: "Smartwatch",
    description:
      "Wearable smart device to track your daily activities and notifications.",
    price: "$299",
  },
];
export default products;
```

Each product has properties like **id**, **name**, **description**, and **price**. This structure helps you manage and display product information consistently.

## Step 3: Create the React Component

Creating a React component involves defining a piece of the UI as a reusable element, which manages its behavior and presentation. For this project, you'll create a component called ProductsView that displays products in either a list or a grid view, controlled by buttons.

**Setting up the Component:**

- Navigate to the **src/** directory in your project.
- Create a new file named `ProductsView.js`. This will be where you define the component to handle product display.
  Develop the Component:
- Begin by importing React and the `useState` hook since you'll manage the view state (list or grid) dynamically.
- Import the products data from your previously created `products.js` file. This import allows the component to access the product data.

```jsx
// src/components/ProductsView.js
import React, { useState } from "react";
import products from "../data/products";

function ProductsView() {
  // Initialize the state to true indicating the default view is grid.
  const [isGridView, setIsGridView] = useState(true);

  // Function to switch to list view
  const setListView = () => {
    setIsGridView(false);
  };

  // Function to switch back to grid view
  const setGridView = () => {
    setIsGridView(true);
  };

  return (
    <div>
      <button onClick={setListView}>List View</button>
      <button onClick={setGridView}>Grid View</button>
      <div className={isGridView ? "grid-container" : "list-container"}>
        {products.map((product) => (
          <div
            key={product.id}
            className={isGridView ? "grid-item" : "list-item"}
          >
            <h3>{product.name}</h3>
            <p>{product.description}</p>
            <p>{product.price}</p>
          </div>
        ))}
      </div>
    </div>
  );
}

export default ProductsView;
```

- **State Management:** `useState` is a Hook that lets you add React state to function components. In this component, `isGridView` is a state variable that determines the current view of the products (grid or list). The initial state is set to `true` indicating the default is grid view.

- **Handling Events:** The component includes two buttons that let users switch views. Each button has an `onClick` event handler (`setListView` and `setGridView`) that updates the `isGridView` state. Changing this state triggers a re-render of the component.

- **Rendering Products:** The `products.map()` function iterates over each product in the data array, rendering a div for each one. The class of this div changes based on the `isGridView` state, which alters its styling according to the CSS definitions.

- **Conditional Class Assignment:** The container div for the products uses a ternary operator to dynamically assign its class based on the `isGridView` state. This changes the layout between a grid and a list, controlled by the CSS classes grid-container and list-container.

## Step 4: Add CSS for Styling

Proper styling is crucial for making the app visually appealing and easy to navigate.

- Update the `App.css` file located in the `src` directory:

```css
/* src/App.css */
.grid-container,
.list-container {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}

.grid-item,
.list-item {
  border: 1px solid #ccc;
  padding: 20px;
  text-align: center;
}

.list-container {
  flex-direction: column;
}

.grid-item {
  flex: 1 1 30%; /* Each item will take roughly one-third of the container width */
}
```

- The `.grid-container` and `.list-container` use flexbox to lay out their children in a row or column.
- The `.grid-item` and `.list-item` have similar styling but will align differently based on the container's direction.

## Conclusion

This guide introduced you to creating interactive React applications using state management, functional components, and CSS styling. By following these steps, you built a simple yet functional app that can toggle between two views, which is a valuable skill in modern web development. This setup not only helps understand the basics of React but also prepares you for more complex tasks in future projects.
