+++
title = 'How to make Network Requests(API Calls) Javascript - Lession 17'
date = 2024-01-31T22:12:30+05:30
draft = false
categories = ['Javascript Learning']
image= "/images/js-network-request.webp"
tags=[
    "Javascript",
    "Javascript Network",
    "Web Development",
    "Frontend Development",
    "Javascript Basics",
    "Javascript Syntax",
    "Javascript Types",
    "Javascript Methods",
    "Network Requests",
    "API Calls"
]
weight = 17
+++

![How to make Network Requests(API Calls) Javascript - Lession 17](/images/js-network-request.webp)

## Introduction 🌱

Network requests in JavaScript are used to communicate with external servers, typically for exchanging data. This is fundamental in web applications for operations like loading data, submitting forms, or interacting with external APIs.

## AJAX (Asynchronous JavaScript and XML)

Before the advent of AJAX (Asynchronous JavaScript and XML), updating a web page with new data typically required reloading the entire page. This process was not only inefficient but also resulted in a less responsive user experience. AJAX changed this paradigm significantly.

AJAX is a technique in web development that allows web applications to send and receive data asynchronously from a server. This means that it's possible to update parts of a web page without reloading the whole page.

## How AJAX Works

**Asynchronous Communication:** AJAX communicates with the server asynchronously. This means that after making a request to the server, the user can continue to use the page and interact with it, while the server processes the request.

**JavaScript and the XMLHttpRequest Object:** AJAX uses JavaScript and the XMLHttpRequest object to send and receive information to and from a web server. This object can send both GET and POST requests to the server and receive various types of data formats in return, including XML, JSON, HTML, and text files.

**Updating Webpages Dynamically:** The received data can then be used to update the content of the webpage dynamically using JavaScript. This dynamic update happens without any page reload, creating a seamless user experience.

## AJAX in Action

With AJAX, when a user performs an action that requires a data update (like submitting a form), JavaScript makes a request to the server. The server processes the request and sends back the data. JavaScript then uses this data to update the specific part of the page, all without needing to reload the page.

```javascript
var xhr = new XMLHttpRequest();
xhr.open("GET", "https://jsonplaceholder.typicode.com/posts/1", true);
xhr.onreadystatechange = function () {
  if (xhr.readyState === 4 && xhr.status === 200) {
    var response = JSON.parse(xhr.responseText);
    console.log(response);
    // Update the DOM based on the response
  }
};
xhr.send();
```

In this example, an XMLHttpRequest is made to a server. When the response is received (and if successful), it's parsed from JSON and used to update the page.

## CRUD Operations and Fetch API in JavaScript

CRUD stands for Create, Read, Update, and Delete. These are the four basic operations of persistent storage in web applications. Each of these operations corresponds to a standard HTTP method used in API calls:

- Create: POST
- Read: GET
- Update: PUT
- Delete: DELETE

## Fetch API

The Fetch API is a modern interface for making network requests in JavaScript. It offers a more powerful and flexible approach than the traditional XMLHttpRequest, used in AJAX. Fetch returns promises, making it better suited for handling asynchronous operations in a more readable and efficient way.

## 1. GET Request with Fetch (Read Operation)

The GET method in HTTP is designed for reading or retrieving data from a server. It is the most common type of request used in web applications, typically for fetching data like user information, posts, comments, or any other data that doesn't require modification. GET requests are simple and straightforward, making them a fundamental part of web API interactions.

The Fetch API offers a modern, powerful way to make GET requests in JavaScript. It's promise-based, making it suitable for handling asynchronous operations efficiently.

Let's use the JSONPlaceholder API to fetch a sample post.

```javascript
fetch("https://jsonplaceholder.typicode.com/posts/1")
  .then((response) => response.json())
  .then((data) => console.log(data));
```

The fetch function is called with the URL of the resource we want to retrieve. For a GET request, we don't need to specify the method explicitly since GET is the default.

In this example, fetch starts by making a GET request to the specified URL. The response received is a Response object, which doesn't contain the actual JSON data yet. The .json() method reads the response stream to completion and converts it into a JSON object.

**Understanding Response and Status Codes**

Responses to GET requests generally include:

**Status Code:** A `200 OK` status code indicates a successful response. Other status codes can indicate redirection, client-side or server-side errors.

**Response Body:** The body of a GET request typically contains the requested data in JSON or XML format. This data can then be used within your application.

## 2. POST Request with Fetch (Create Operation)

In web development, a POST request is commonly used to create new resources on the server. This could be anything from adding a new record in a database, submitting form data, or creating a new user account. The POST method sends data to the server, typically in the body of the request.

The Fetch API simplifies sending POST requests in JavaScript. It allows you to send data to a server in an asynchronous manner, and handle the response.

Let's create a new post using the JSONPlaceholder API, a fake online REST API for testing and prototyping.

```javascript
fetch("https://jsonplaceholder.typicode.com/posts", {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
    title: "New Post",
    body: "This is the content of the post.",
    userId: 1,
  }),
})
  .then((response) => {
    console.log("Status Code:", response.status); // Status code of the response
    return response.json();
  })
  .then((json) => console.log("Response Data:", json))
  .catch((error) => console.error("Error:", error));
```

In this snippet:

- We specify the method as 'POST' in the fetch options.
- Headers are set to indicate that the request body format is JSON.
- The request body contains the data to be sent, encoded as a JSON string.
- Upon receiving a response, we first log the status code, which is usually 201 Created for successful POST requests indicating that a new resource was created.
- We then convert the response to JSON and log it. This JSON typically contains the data that was sent, often with additional information like an id assigned by the server.

When a POST request is successfully processed by the server, the response typically includes:

**Status Code:** 201 Created is a common response status code indicating that the request was successful and led to the creation of a new resource. Other codes might be returned depending on the server's implementation.

**Response Body:** Often, the server responds with the created resource's data, including any new identifiers or timestamps generated by the server.

## 3. PUT Request with Fetch (Update Operation)

The PUT method in HTTP is primarily used for updating existing resources on the server. It is a standard method for conveying data modifications, and it typically replaces the entire resource with the updated data.

To update a resource using the Fetch API, you need to specify the method as 'PUT' and provide the updated data in the request body.

Let's update a post using the JSONPlaceholder API:

```javascript
fetch("https://jsonplaceholder.typicode.com/posts/1", {
  method: "PUT",
  headers: {
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
    title: "Updated Post",
    body: "This is the updated content of the post.",
    userId: 1,
  }),
})
  .then((response) => {
    console.log("Status Code:", response.status); // Status code of the response
    return response.json();
  })
  .then((json) => console.log("Response Data:", json))
  .catch((error) => console.error("Error:", error));
```

In this example:

- We specify the method as 'PUT' and set the appropriate headers.
- The body of the request contains the updated data in JSON format.
- The response is then processed and displayed, typically showing the updated resource.

When a PUT request is successfully processed by the server, the response typically includes:

**Status Code:** 200 OK is a common response status code indicating that the request was successful. Other codes might be returned depending on the server's implementation.

**Response Body:** The server typically returns the updated resource's data, including any new identifiers or timestamps generated by the server.

## Difference Between PUT and PATCH

While both PUT and PATCH are used for updating resources, there's a key difference in how they operate:

**PUT:** This method replaces the entire target resource with the supplied data. If certain attributes are omitted in the request, they are typically cleared or reset to their default on the server.

PUT Example:

```json
{ "title": "New Title", "body": "New body" }
```

Here, only the title and body are specified, and other attributes, if any, might be removed or reset.

**PATCH:** Unlike `PUT`, `PATCH` is used for partial updates. Only the specified fields in the request are updated, leaving the rest of the resource unchanged.

**PATCH Example:**

```json
{ "title": "New Title" }
```

In this case, only the title is updated, and all other aspects of the resource remain as they were.

Understanding how to use the PUT method with the Fetch API is crucial for implementing update functionality in web applications. While PUT and PATCH both serve to update resources, the choice between them depends on whether you need to update the entire resource (PUT) or just modify certain parts of it (PATCH). This understanding is key to effective and efficient API interactions in modern web development.

## 4. DELETE Request with Fetch (Delete Operation)

In web development, the DELETE method is used to remove resources from the server. It's a crucial part of CRUD operations (Create, Read, Update, Delete), enabling the removal of data like user accounts, posts, or other entities. The DELETE method signals the server to delete the resource identified by the provided URL.

Using the Fetch API to send a DELETE request is straightforward. Unlike POST or PUT requests, DELETE requests typically don't require a body, as the resource to be deleted is specified in the URL.

Let’s demonstrate a DELETE request using the JSONPlaceholder API:

```javascript
fetch("https://jsonplaceholder.typicode.com/posts/1", {
  method: "DELETE",
})
  .then((response) => {
    console.log("Status Code:", response.status); // Status code of the response
    return response.json();
  })
  .then((json) => console.log("Response Data:", json))
  .catch((error) => console.error("Error:", error));
```

In this example:

- We specify the method as 'DELETE'.
- The URL includes the ID of the resource to be deleted (/posts/1).
- After sending the request, we log the status code. A successful `DELETE` request typically returns a 200 OK or 204 No Content status code, indicating that the resource was successfully deleted.
- The response body of a `DELETE` request is often empty, as the resource no longer exists.

**Handling Responses and Status Codes**

When handling responses from DELETE requests, it's important to check the status code to confirm successful deletion. Common status codes include:

**200 OK:** Indicates that the request was successful and the server's response contains a message body.

**204 No Content:** Similar to 200, but the server has not returned any content. This is common for DELETE operations, where there's nothing to show once a resource is removed.

The DELETE method, as part of the Fetch API, is essential for removing resources in web applications. It's a straightforward process that enhances the dynamic nature of web applications, allowing for real-time data management. Understanding how to properly send DELETE requests and handle responses is key to effectively managing server-side data in modern web development.

## Conclusion

In summary, the Fetch API provides a modern, efficient, and straightforward way to perform CRUD (`Create`, `Read`, `Update`, `Delete`) operations in web development. Whether it's adding new data with POST, retrieving data with GET, updating information with `PUT/PATCH`, or removing data with DELETE, Fetch handles these tasks seamlessly with its promise-based structure. This approach not only simplifies coding asynchronous requests but also enhances the overall user experience by enabling dynamic and responsive interactions with server-side data. Mastering these operations with the Fetch API is crucial for any developer looking to build interactive and data-driven web applications.


