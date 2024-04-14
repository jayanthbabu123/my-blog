+++
title = 'Implementing Cart Functionality in React with Context API'
date = 2024-04-14T09:59:57+05:30
draft = false
+++

Implementing a shopping cart functionality using React's Context API allows you to manage the cart items across your application seamlessly. Below, I’ll guide you step-by-step on how to set up a cart context, add items to the cart, and display the cart count in the header.

## Step 1: Create the Cart Context

First, you need to create a context that will manage the cart items and provide functions to manipulate the cart contents.

**Setting Up CartContext**

**Create the Context:** Define a new context that will hold the cart items.

**CartProvider Component:** This component will provide the cart state and functions to modify it to other components.

**useCart Custom Hook:** This hook simplifies accessing the cart context from any component.

Here’s how you can set up and use the CartContext:

```jsx
// src/CartContext.js
import { createContext, useContext, useState } from "react";

const CartContext = createContext();

export const CartProvider = ({ children }) => {
  const [cartItems, setCartItems] = useState([]);

  const addToCart = (item) => {
    setCartItems((prevItems) => [...prevItems, item]);
  };

  const removeFromCart = (itemId) => {
    setCartItems((prevItems) => prevItems.filter((item) => item.id !== itemId));
  };

  const clearCart = () => {
    setCartItems([]);
  };

  return (
    <CartContext.Provider
      value={{ cartItems, addToCart, removeFromCart, clearCart }}
    >
      {children}
    </CartContext.Provider>
  );
};

export const useCart = () => useContext(CartContext);

export default CartContext;
```

## Step 2: Modify the App Component to Include CartProvider

You'll need to wrap your application's component tree with the CartProvider to make sure the cart context is accessible throughout your application. This involves a slight restructuring of your existing setup to nest the CartProvider within the UserContext.Provider.

Here's how to integrate the CartProvider into your existing App component:

```jsx
// src/App.js
import React from "react";
import { BrowserRouter, Routes, Route } from "react-router-dom";
import Header from "./Components/Header";
import Dashboard from "./Pages/Dashboard/Dashboard";
import Home from "./Pages/Home/Home";
import Login from "./Pages/Login/Login";
import NotFound from "./Pages/NotFound/NotFound";
import Profile from "./Pages/Profile/Profile";
import SignUp from "./Pages/SignUp/SignUp";
import UserContext from "./UserContext";
import { CartProvider } from "./CartContext"; // Make sure to import CartProvider

const App = () => {
  return (
    <>
      <UserContext.Provider value={"babu"}>
        <CartProvider>
          {" "}
          {/* CartProvider wrapped inside UserContext.Provider */}
          <BrowserRouter>
            <div>
              <Header />
              <Routes>
                <Route path="/" element={<Login />} />
                <Route path="/home" element={<Home />} />
                <Route path="/dashboard" element={<Dashboard />} />
                <Route path="/login" element={<Login />} />
                <Route path="/profile" element={<Profile />} />
                <Route path="/signup" element={<SignUp />} />
                <Route path="*" element={<NotFound />} />
              </Routes>
            </div>
          </BrowserRouter>
        </CartProvider>
      </UserContext.Provider>
    </>
  );
};

export default App;
```

## Step 3: Add Items to the Cart

Implementing shopping cart functionality in React applications is streamlined by using the Context API, which allows for seamless management of cart items across all components. This guide will walk you through setting up a cart context, adding items to the cart, and displaying the cart count in the header.

**1. Set Up a Sample Product Array**

First, you'll need an array of products that your application can display. Each product in the array should have properties like id, name, description, price, and image URL.

```jsx
const products = [
  {
    id: 1,
    name: "Product 1",
    description: "Description of product 1",
    price: 9.99,
    image: "https://example.com/product1.jpg",
  },
  {
    id: 2,
    name: "Product 2",
    description: "Description of product 2",
    price: 19.99,
    image: "https://example.com/product2.jpg",
  },
  {
    id: 3,
    name: "Product 3",
    description: "Description of product 3",
    price: 29.99,
    image: "https://example.com/product3.jpg",
  },
];
```

**2. Create a ProductCard Component**

This component will display an individual product. It should include an image, description, price, and an "Add to Cart" button.

```jsx
// src/components/ProductCard.js
import React from "react";
import { useCart } from "../CartContext"; // Make sure to import useCart from your CartContext

function ProductCard({ product }) {
  const { addToCart } = useCart();

  const handleAddToCart = () => {
    addToCart(product);
  };

  return (
    <div className="card" style={{ width: "18rem" }}>
      <img src={product.imageUrl} className="card-img-top" alt={product.name} />
      <div className="card-body">
        <h5 className="card-title">{product.name}</h5>
        <p className="card-text">{product.description}</p>
        <p className="card-text">${product.price}</p>
        <button className="btn btn-primary" onClick={handleAddToCart}>
          Add to Cart
        </button>
      </div>
    </div>
  );
}

export default ProductCard;
```

**3. Display Products on a Product Page**

Create a ProductsPage component that uses the ProductCard to display each product.

```jsx
// src/pages/ProductsPage.js
import React from "react";
import ProductCard from "../components/ProductCard";

function ProductsPage() {
  const products = [
    {
      id: 1,
      name: "Laptop",
      description: "High-performance laptop",
      price: 999.99,
      imageUrl: "https://example.com/laptop.jpg",
    },
    {
      id: 2,
      name: "Smartphone",
      description: "Latest model smartphone",
      price: 499.99,
      imageUrl: "https://example.com/smartphone.jpg",
    },
    {
      id: 3,
      name: "Smartwatch",
      description: "Your fitness companion",
      price: 199.99,
      imageUrl: "https://example.com/smartwatch.jpg",
    },
  ];

  return (
    <div className="container mt-5">
      <div className="row">
        {products.map((product) => (
          <div key={product.id} className="col-md-4 mb-4">
            <ProductCard product={product} />
          </div>
        ))}
      </div>
    </div>
  );
}

export default ProductsPage;
```

## Step 4: Update the Header Component to Display Cart Items Count

Modify the header component to show the number of items in the cart. Use the useCart hook to access the cart items.

```jsx
// src/Components/Header.js
import React from "react";
import { Link } from "react-router-dom";
import { useCart } from "../CartContext";

function Header() {
  const { cartItems } = useCart();

  return (
    <nav className="navbar navbar-expand-lg navbar-light bg-light">
      <Link className="navbar-brand" to="/">
        Home
      </Link>
      <div className="collapse navbar-collapse">
        <ul className="navbar-nav mr-auto">
          <li className="nav-item">
            <Link className="nav-link" to="/checkout">
              Checkout
            </Link>
          </li>
        </ul>
        <div className="navbar-text">Cart Items: {cartItems.length}</div>
      </div>
    </nav>
  );
}

export default Header;
```

By following these steps, you have successfully integrated a cart functionality into your React application using the Context API. This allows for seamless state management of cart items, ensuring a smooth user experience across different components of your application.
