+++
title = 'Event Delegation in Javascript'
date = 2024-02-09T22:45:15+05:30
draft = false
+++

Event delegation in JavaScript is a technique where instead of adding an event listener to each individual element, you add a single event listener to a parent element to handle events for multiple children. This allows you to handle events for multiple elements without having to add multiple listeners to each element.

Event delegation in JavaScript leverages the event bubbling mechanism to listen for events at a higher (parent) level rather than attaching event listeners to individual child elements. It's an efficient way to handle events for multiple elements that share the same behavior, particularly useful when you have dynamic content (elements added or removed after the initial page load).

This approach minimizes the number of event listeners you need, improving performance and memory usage. It also simplifies managing event listeners for elements that are dynamically added to the DOM.

Here's a complete example to illustrate event delegation in action:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Event Delegation Example</title>
  </head>
  <body>
    <div id="buttonsContainer">
      <button class="actionButton">Button 1</button>
      <button class="actionButton">Button 2</button>
      <button class="actionButton">Button 3</button>
    </div>

    <script>
      document
        .getElementById("buttonsContainer")
        .addEventListener("click", function (event) {
          if (event.target && event.target.matches(".actionButton")) {
            alert(`You clicked ${event.target.textContent}!`);
          }
        });
    </script>
  </body>
</html>
```
In this example, instead of attaching an event listener to each button, we attach a single event listener to the buttonsContainer. The event listener checks if the clicked target (event.target) is one of the buttons (event.target.matches('.actionButton')). If it is, it displays an alert showing which button was clicked.

This method is especially useful for handling events on elements that might not exist when the page loads but could be added dynamically later. It simplifies managing event listeners and ensures that the webpage performs efficiently, even with a large number of interactive elements.