+++
title = 'Websockets in Javascript'
date = 2024-02-10T07:08:33+05:30
draft = false
+++

WebSockets are a powerful Web API that enables a persistent, two-way communication channel between a web browser and a server. Unlike traditional HTTP requests, which are short-lived and require new connections for each exchange, WebSockets establish a single, long-lived connection, allowing for real-time data exchange without constant refreshing or polling.

WebSocket URLs use the prefix `"ws://"` for unsecured connections and `"wss://"` for secured connections, mirroring the `"http://"` and `"https://"` conventions of HTTP. Using `"wss://"` is advisable when dealing with sensitive data or in production environments to ensure the communication is encrypted.

WebSockets run as part of the Web API, similar to XMLHttpRequest and the Fetch API, and operate on the browser's main thread. However, they are designed to be non-blocking and efficient, meaning they don't interrupt the user interface or other operations. Despite running on the main thread, they are capable of maintaining a smooth user experience.

WebSockets are not supported in Internet Explorer. However, they are supported in Chrome, Firefox, and Safari.

Here's a simple example of how to establish a WebSocket connection and interact with it in JavaScript:

```javascript
// Establishing a WebSocket connection to the server
const socket = new WebSocket('wss://yourserver.com/path');

// Event listener for connection open
socket.onopen = function() {
  console.log('Connection established');
  // Sending a message to the server once the connection is open
  socket.send('Hello Server!');
};

// Event listener for receiving messages from the server
socket.onmessage = function(event) {
  console.log('Received message:', event.data);
  // Here you can handle incoming messages
};

// Event listener for handling connection errors
socket.onerror = function(error) {
  console.error('WebSocket Error:', error);
};

// Event listener for connection close
socket.onclose = function(event) {
  console.log('Connection closed', event.reason);
};

```
In this code, a WebSocket connection is initiated using the WebSocket constructor with a URL beginning with `"wss://"`. The `onopen`, `onmessage`, `onerror`, and `onclose` event listeners are set up to handle the connection opening, messages from the server, errors, and the closing of the connection, respectively. The `send()` method is used to send messages to the server.

