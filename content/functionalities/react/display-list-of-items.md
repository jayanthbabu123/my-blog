+++
title = 'Display List of Items in React JS'
date = 2024-04-14T21:40:54+05:30
draft = false
+++

In modern web applications, displaying lists of items like products is a common requirement. React, with its component-based architecture, makes it straightforward to render dynamic data effectively. In this guide, we will learn how to represent a list of products in two different formats: as cards (which are great for e-commerce sites) and as a simple list view (suitable for admin panels or detailed listings). We will use JSON data to simulate a real-world scenario where data might be fetched from an API.

## Step 1: Declaring List of Products as JSON

First, we need some data to work with. In a real application, this data might come from a server, but for this example, we'll define a static list of products directly in our code using JSON format. This data will be used to populate our product cards and list views.

Create a file or define a constant in your component file:

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

## Step 2: Creating a Component That Renders List of Products as Cards

With our product data defined, let's create a React component to display each product as a card. This is a common design pattern in e-commerce sites where products need to be visually appealing and information should be clear at a glance.

Create a new component ProductCard.js and a parent component ProductsGrid.js that uses it:

```js
// src/components/ProductCard.js
import React from "react";

function ProductCard({ product }) {
  return (
    <div className="card">
      <div className="card-body">
        <h5 className="card-title">{product.name}</h5>
        <p className="card-text">{product.description}</p>
        <p className="card-text">{product.price}</p>
      </div>
    </div>
  );
}

export default ProductCard;
```

```js
// src/components/ProductsGrid.js
import React from "react";
import ProductCard from "./ProductCard";
import products from "../data/products";

function ProductsGrid() {
  return (
    <div className="grid">
      {products.map((product) => (
        <ProductCard key={product.id} product={product} />
      ))}
    </div>
  );
}

export default ProductsGrid;
```

In these components, ProductsGrid maps over the products array and renders a ProductCard for each product, passing the product data as a prop.

## Step 3: List of Products as ListView

Sometimes, a more detailed or simplistic list view is preferable, especially in admin panels or less graphic-intensive parts of an application. Let’s create a list view for the same products.

```jsx
// src/components/ProductsList.js
import React from "react";
import products from "../data/products";

function ProductsList() {
  return (
    <ul>
      {products.map((product) => (
        <li key={product.id}>
          {product.name} - {product.description} - {product.price}
        </li>
      ))}
    </ul>
  );
}

export default ProductsList;
```

In this guide, we've seen how to display lists of products in React using both card and list views. By leveraging React's component model, we can efficiently render dynamic data in various formats based on the design requirements of the application. This flexibility is one of the many reasons why React is so powerful for building interactive and dynamic web applications. Whether you're building a complex e-commerce platform or a simple data display interface, React provides the tools needed to do it effectively and elegantly.