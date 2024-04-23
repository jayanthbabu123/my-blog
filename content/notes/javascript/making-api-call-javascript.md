+++
title = 'How to Make API Calls in JavaScript'
date = 2024-04-23T12:58:15+05:30
draft = false
+++

## Introduction to Network Requests in JavaScript

In the world of web development, the ability to interact with remote servers is fundamental. Whether fetching data, sending information, or updating content, making network requests is crucial for dynamic, interactive web applications. Traditionally, these requests were handled using `XMLHttpRequest`, a complex but powerful interface that allowed developers to retrieve data from URLs without having to do a full page refresh. This method, while effective, often led to cumbersome code, especially when dealing with complex data exchanges or asynchronous operations.

As web technologies evolved, so did the tools for making these requests. Enter the Fetch API, a modern approach introduced to simplify the process and improve the handling of network requests in JavaScript. The fetch API provides a more efficient and readable method for making HTTP calls and is designed to handle promises natively, offering a significant upgrade over the older XMLHttpRequest style.

Understanding how to utilize the fetch API effectively is now considered an essential skill for modern web developers. It not only simplifies code but also enhances functionality with its promise-based structure, making it easier to manage asynchronous operations and handle data more cleanly.

## Understanding Network Requests

A network request in web development is a call made from a client (usually a web browser) to a server. This request can fetch data, submit data, update data, or delete data. Traditionally, this was done using `XMLHttpRequest`, a JavaScript object that allows you to interact with servers even after a web page has loaded. While powerful, `XMLHttpRequest` can be complex and verbose, especially when dealing with modern web applications.

## Introduction to Fetch API

The `fetch` API provides a more modern and powerful alternative to `XMLHttpRequest` for making HTTP requests. It returns promises and supports a cleaner, more functional style of asynchronous operations. `fetch` is versatile, handling various types of requests: `GET`, `POST`, `PUT`, and `DELETE`, each serving different purposes in web development.

## Historical Context and Introduction

The Fetch API started to gain traction around 2015, as part of the living standard. It is a modern specification developed by the WHATWG (Web Hypertext Application Technology Working Group), aiming to provide a more powerful and flexible feature set.

## Technical Underpinnings

`XHR Under the Hood?` Unlike common misconceptions, the Fetch API does not use `XMLHttpRequest` under the hood. It is a completely new implementation built on the `Streams` API, allowing it to handle request and response bodies as streams. This approach offers more fine-grained control over the `request/response` lifecycle and supports asynchronous data handling more robustly than `XHR`.

`Support and Compatibility:` Most modern browsers support the Fetch API, but it's not available in Internet Explorer. Developers often use polyfills to add support for Fetch in environments that do not natively support it.

## Checking for Fetch API Availability

To determine whether the Fetch API is available in a given browser environment, you can check the existence of fetch on the window object. This is a straightforward way to programmatically ascertain support:

```js
if ("fetch" in window) {
  console.log("Fetch API is supported in this browser.");
} else {
  console.log("Fetch API is not supported in this browser.");
}
```

This check helps ensure that your application can use Fetch where it is available, and potentially fall back to a polyfill or XMLHttpRequest if necessary.

## Making GET Requests with the Fetch API

**What is a GET Request?**

A GET request is used primarily to retrieve data from a specified resource. It's the most common type of HTTP request, designed to fetch data without modifying any data stored on the server. In the context of the Fetch API, a GET request can be made explicitly by setting the method attribute to 'GET' or by default, since GET is the default method used by Fetch.

**How to Make a GET Request with Fetch**

Using Fetch to make a GET request is straightforward. Here’s how you can handle it effectively when interacting with your product management system:

```js
fetch("http://localhost:5000/api/products")
  .then((response) => {
    if (!response.ok) {
      throw new Error("Network response was not ok: " + response.statusText);
    }
    return response.json(); // Convert the response to JSON
  })
  .then((data) => console.log("All Products:", data)) // Process and display the data
  .catch((error) => console.error("Failed to fetch data:", error));
```

In this example:

`Initiate Fetch:` The fetch function is called with the URL of the data you wish to retrieve. By default, this is a GET request.

`Handle Response: `The first .then() checks if the response was successful (response.ok). If the response indicates an error (e.g., a `404` or `500` status code), it throws an error. Otherwise, it proceeds to parse the response body as JSON with response.json().

`Process Data:` The second .then() is where you handle the parsed data, which is now a JavaScript object.

`Error Handling:` The .catch() method is used to catch any errors in the network request or data processing.

Here’s how you can make a comprehensive GET request using Fetch, including an explicit mention of the request type:

```js
fetch("http://localhost:5000/api/products", { method: "GET" }) // Explicitly stating the method
  .then((response) => {
    if (!response.ok) {
      throw new Error("Network response was not ok: " + response.statusText);
    }
    return response.json(); // Parse the response as JSON
  })
  .then((data) => console.log("All Products:", data)) // Handle the JSON data
  .catch((error) => console.error("Error during fetch:", error));
```

**Including Headers in a GET Request**

Sometimes, you may need to include headers in your GET request, such as authentication tokens or other information needed by the server:

```js
fetch("http://localhost:5000/api/products", {
  headers: {
    Authorization: "Bearer your_token_here",
    "Content-Type": "application/json",
  },
})
  .then((response) => response.json())
  .then((data) => console.log("All Products:", data))
  .catch((error) => console.error("Error:", error));
```

In this setup, the headers option includes necessary headers like `Authorization` for security tokens and `Content-Type` to specify the data format. These headers ensure that the server interprets the request correctly and that secure endpoints are properly authenticated.

## Handling URL Parameters

For GET requests that require parameters, you do not use the body of the request. Instead, you append the parameters to the URL:

```js
const queryParams = new URLSearchParams({
  search: "query",
  limit: "10",
}).toString();

const url = `https://api.example.com/data?${queryParams}`;

fetch(url)
  .then((response) => response.json())
  .then((data) => console.log(data))
  .catch((error) => console.error("Error:", error));
```

In this code snippet, `URLSearchParams` is used to construct query parameters in a clean and safe manner, ensuring they are properly encoded. This string is then appended to the URL.

Making GET requests using the Fetch API is a fundamental skill for web developers, particularly when interacting with RESTful APIs like your product management system. By understanding how to structure these requests correctly, developers can efficiently retrieve data and handle different server responses, enhancing the functionality and responsiveness of web applications.

## Making POST Requests with the Fetch API

**What is a POST Request?**

A POST request is used to send data to a server to create a new resource. It's a critical type of HTTP request for web applications that allow users to submit data, such as forms. When using the Fetch API, a POST request requires setting the method attribute to 'POST' and typically includes data in the body of the request that you want to send to the server.

## Adding a Single Product

Here’s how you can make a POST request to add a new product to your database:

```js
const newProduct = {
  name: "New Product",
  price: 19.99,
  description: "A great product",
  image: "http://example.com/product.jpg",
  available: true,
  category: "electronics",
};

fetch("http://localhost:5000/api/products", {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
  },
  body: JSON.stringify(newProduct),
})
  .then((response) => {
    if (!response.ok) {
      throw new Error("Failed to create product: " + response.statusText);
    }
    return response.json();
  })
  .then((data) => console.log("Product Created:", data))
  .catch((error) => console.error("Error creating product:", error));
```

- **Method Set to POST:** This explicitly tells the server that the intent of the request is to create a new resource.
- **Headers:** The Content-Type header is crucial as it tells the server what kind of data is being sent (in this case, JSON).
- **Body:** The body contains the data of the new product, which is stringified into JSON format.
- **Handling Responses:** After sending the request, the response is processed to check if it was successful and to parse the returned data.

## Adding Multiple Products

If your API supports adding multiple products at once, you can adjust the body to include an array of product objects:

```js
const products = [
  {
    name: "Product One",
    price: 50,
    description: "Quality item",
    image: "http://example.com/p1.jpg",
    available: true,
    category: "home",
  },
  {
    name: "Product Two",
    price: 75,
    description: "Luxury item",
    image: "http://example.com/p2.jpg",
    available: false,
    category: "garden",
  },
];

fetch("http://localhost:5000/api/products/bulk", {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
  },
  body: JSON.stringify(products),
})
  .then((response) => response.json())
  .then((data) => console.log("Bulk Products Added:", data))
  .catch((error) => console.error("Error adding bulk products:", error));
```

## Including Additional Headers

In scenarios where authentication is required or other metadata needs to be included, you may need to add additional headers to your POST request:

```js
const newProduct = {
  name: "New Product",
  price: 19.99,
  description: "A great product",
  image: "http://example.com/product.jpg",
  available: true,
  category: "electronics",
};
fetch("http://localhost:5000/api/products", {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
    Authorization: "Bearer your_access_token", // Assuming bearer token authentication
  },
  body: JSON.stringify(newProduct),
})
  .then((response) => response.json())
  .then((data) => console.log("Product created:", data))
  .catch((error) => console.error("Error during fetch:", error));
```

Making POST requests using the Fetch API is essential for interacting with APIs where you need to submit data to create new resources. Properly configuring the request by setting the correct method, headers, and body ensures that your data is transmitted correctly to the server and that the application can react appropriately to the responses received. This capability is foundational for any web developer looking to build interactive and dynamic web applications, especially those involving data management like your product system.

## Making PUT Requests with the Fetch API

**What is a PUT Request?**

A PUT request is used to send data to a server to update an existing resource. It is idempotent, meaning that making the same PUT request multiple times will always produce the same result. Unlike POST requests, which can create a new resource each time, a PUT request should only update the data of an existing resource.

## How to Make a PUT Request with Fetch

To update a product's details in your API, a PUT request requires specifying the method, including appropriate headers, and providing a body with updated data. Here's how you can structure a PUT request to update a product:

```js
const updatedProduct = {
  name: "Updated Product Name",
  price: 149.99,
  description: "Updated product description",
  image: "http://example.com/new-image.png",
  available: true,
  category: "updated-category",
};

const productId = "12345"; // Assuming '12345' is the ID of the product to update

fetch(`http://localhost:5000/api/products/${productId}`, {
  method: "PUT",
  headers: {
    "Content-Type": "application/json",
  },
  body: JSON.stringify(updatedProduct),
})
  .then((response) => {
    if (!response.ok) {
      throw new Error("Network response was not ok: " + response.statusText);
    }
    return response.json();
  })
  .then((data) => console.log("Product updated:", data))
  .catch((error) => console.error("Failed to update product:", error));
```

- **Method Specification:** The method is set to "PUT" to clearly indicate that the request is intended to update a resource.
- **Headers:** Similar to a POST request, the Content-Type header is specified as application/json to let the server know the format of the data being sent.
- **Body:** The body contains the JSON string of the updatedProduct, which includes all the new details that need to be updated on the server.
- **URL Parameter:** The URL includes the productId to specify which product is to be updated.
- **Response and Error Handling:** Responses are checked for success status, parsed for data, and errors are managed.

## Including Additional Headers for Authentication

If your API requires authentication for making changes, you'll need to include an authorization header:

```js
const updatedProduct = {
  name: "Updated Product Name",
  price: 149.99,
  description: "Updated product description",
  image: "http://example.com/new-image.png",
  available: true,
  category: "updated-category",
};
fetch(`http://localhost:5000/api/products/${productId}`, {
  method: "PUT",
  headers: {
    "Content-Type": "application/json",
    Authorization: "Bearer your_access_token", // Assuming bearer token authentication
  },
  body: JSON.stringify(updatedProduct),
})
  .then((response) => {
    if (!response.ok) {
      throw new Error("Network response was not ok: " + response.statusText);
    }
    return response.json();
  })
  .then((data) => console.log("Product updated:", data))
  .catch((error) => console.error("Failed to update product:", error));
```

Making PUT requests using the Fetch API allows you to efficiently update data on the server. Proper configuration of these requests ensures that data integrity is maintained and that the server's responses can be handled effectively. This functionality is crucial for maintaining dynamic content in applications that manage resources, such as your product management system.

## Making DELETE Requests with the Fetch API

**What is a DELETE Request?**

A DELETE request is used to remove an existing resource from a server. It's a crucial operation in many applications, particularly those involving content management or data maintenance, where the ability to remove data cleanly and efficiently is important.

## Deleting a Specific Product

Here's how you can structure a DELETE request to remove a specific product by its ID:

```js
const productId = "12345"; // Assuming '12345' is the ID of the product to delete

fetch(`http://localhost:5000/api/products/${productId}`, {
  method: "DELETE",
})
  .then((response) => {
    if (!response.ok) {
      throw new Error("Network response was not ok: " + response.statusText);
    }
    return response.json();
  })
  .then((data) => console.log("Product deleted successfully:", data))
  .catch((error) => console.error("Failed to delete product:", error));
```

- **Method Specification:** The method is set to "DELETE" to clearly indicate that the request is intended to remove a resource.
- **URL Parameter:** The URL includes the productId to specify which product is to be deleted.
- **Response and Error Handling:** Responses are checked for success status, and the success message is processed. Errors are managed to handle cases where the product might not exist or the server encounters an issue.

## Deleting All Products

If your API supports deleting all products at once, here’s how you might structure such a request, though this should be used with caution due to its potential impact:

```js
fetch("http://localhost:5000/api/products", {
  method: "DELETE",
})
  .then((response) => {
    if (!response.ok) {
      throw new Error("Network response was not ok: " + response.statusText);
    }
    return response.json();
  })
  .then((data) => console.log("All products deleted successfully:", data))
  .catch((error) => console.error("Failed to delete all products:", error));
```

## Including Additional Headers for Authentication

For operations that affect the data significantly, like DELETE requests, you may need to include an authorization header to ensure that the request is authenticated:

```js
fetch(`http://localhost:5000/api/products/${productId}`, {
  method: "DELETE",
  headers: {
    Authorization: "Bearer your_secure_token", // Include the token if necessary
  },
})
  .then((response) => response.json())
  .then((data) => console.log("Product deleted successfully:", data))
  .catch((error) => console.error("Error during fetch:", error));
```

Using the Fetch API to make DELETE requests allows you to manage server-side resources effectively, ensuring that unwanted or obsolete data can be removed securely and efficiently. Properly configuring these requests is essential, particularly for operations that can significantly impact your data landscape. This functionality is a critical component of dynamic web applications, particularly in scenarios like product management where accurate data maintenance is crucial.

## Conclusion

This guide provides comprehensive details on how to interact with a product management API using the Fetch API. These operations cover retrieving, adding, updating, and deleting products, which are essential functionalities for managing an online product catalog. By using these examples, developers can effectively integrate network operations into their web applications, ensuring dynamic data handling and responsive user interactions.
