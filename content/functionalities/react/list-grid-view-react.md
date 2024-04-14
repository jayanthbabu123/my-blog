+++
title = 'Creating a Toggleable List and Grid View in React'
date = 2024-04-14T22:23:00+05:30
draft = false
+++

Displaying products in both list and grid formats allows users to choose their preferred viewing style, enhancing usability and accessibility. This approach leverages React's component-based architecture to dynamically switch between views based on user interaction. We will use a static list of products to simulate a real-world application fetching data from a backend.

## Step 1: Declare a List of Products

First, we need a dataset to work with. Let’s start by defining a static list of products. In a real-world scenario, this data might come from an API, but for simplicity, we'll define it directly in our project.

Create a new file to hold our product data:

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

This array simulates a typical e-commerce product list, with each product having an ID, name, description, and price.

## Step 2: Creating Components for Grid and ListView

Next, we'll create a React component that can render this data in both a grid and a list format. We will implement a toggle button that lets users switch between these views.

Create a new component ProductsView.js:

```jsx
// src/components/ProductsView.js
import React, { useState } from "react";
import products from "../data/products";

function ProductsView() {
  const [isGridView, setIsGridView] = useState(true); // Default view is grid

  return (
    <div>
      <button onClick={() => setIsGridView(!isGridView)}>
        Switch to {isGridView ? "List" : "Grid"} View
      </button>
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

In this component:

**Toggle Button:** Allows users to switch between grid and list views.

**Dynamic CSS Classes:** Conditional rendering of CSS classes based on isGridView state changes the layout of the product display.

## Conclusion

Implementing a toggleable list and grid view in React not only improves the flexibility and user-friendliness of your application but also showcases the power of React's state management and conditional rendering. This feature is particularly useful in e-commerce sites and product galleries, where users might prefer different methods of browsing products.

By leveraging React’s state management and conditional rendering capabilities, developers can create highly interactive and adaptive user interfaces that respond intuitively to user preferences, enhancing the user experience and engagement.
