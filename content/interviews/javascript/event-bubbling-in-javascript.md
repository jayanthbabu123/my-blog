+++
title = 'Event Bubbling in Javascript'
date = 2024-02-10T06:41:35+05:30
draft = false
+++

Event bubbling in JavaScript is a mechanism where an event triggered on a DOM element propagates up through its ancestors in the DOM tree. This means that if you click on a child element, the event will first be handled by the child, and then it will "bubble up" to its parent, and then to its parent's parent, and so on, until it reaches the root of the document. This behavior allows for a technique called event delegation, where a single event listener can be attached to a parent element to manage events for multiple child elements, improving performance and memory efficiency.

To illustrate event bubbling, let's consider a simple HTML structure with a button inside a div:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Event Bubbling Example</title>
  </head>
  <body>
    <div id="parentDiv" style="padding: 20px; background-color: #f0f0f0;">
      Click me or the button!
      <button id="childButton">Click Me!</button>
    </div>

    <script>
      document
        .getElementById("parentDiv")
        .addEventListener("click", function () {
          alert("Div clicked!");
        });

      document
        .getElementById("childButton")
        .addEventListener("click", function (event) {
          alert("Button clicked!");
          // event.stopPropagation(); // Uncomment this line to stop bubbling up
        });
    </script>
  </body>
</html>
```

In this example, clicking the button triggers the alert for the button click and then triggers the alert for the div click due to event bubbling. If you want to prevent the event from bubbling up, you can call `event.stopPropagation()` in the child element's event handler. This method stops the event from moving up the DOM tree, preventing any parent handlers from being notified of the event.

Understanding event bubbling is essential for efficient event handling in web applications. It allows developers to write less code, attach fewer event handlers, and, when used with event delegation, can improve the performance of web applications, especially those with dynamically generated content.


