+++
title = 'Javascript Window Document - Lession 13'
date = 2024-01-29T23:18:16+05:30
draft = false
categories = ['Javascript Learning']
image= "/images/js-window-document.webp"
tags=[
    "Javascript",
    "Javascript Window",
    "Javascript Document",
    "Web Development",
    "Frontend Development",
    "Javascript Basics",
    "Javascript Syntax",
    "Javascript Types",
    "Javascript Methods",
    "Window Methods",
    "Document Methods"
]
weight = 13
+++

## Introduction 🌱

The Window object in JavaScript is an essential element in web development. It serves as the global object in a browser environment, meaning that you can access it from anywhere in your JavaScript code. Each browser tab is represented by its own Window object, and the properties of this object can be accessed and manipulated using JavaScript.

The `window` object is the global object in JavaScript. It provides access to all the properties and methods of the browser window. Accessing the Window object is straightforward as it is automatically available in the global scope. Here's a basic example:

```javascript
console.log(window);
```

Key Properties and Methods of the Window Object

## 1. Window Size

The properties `innerWidth` and `innerHeight` provide the width and height of the content area of the browser window, excluding toolbars and scrollbars. These are particularly useful for responsive web design, where the layout needs to adjust to different screen sizes.

```javascript
console.log(window.innerWidth); // Outputs: 1280
console.log(window.innerHeight); // Outputs: 720
```

The properties `outerWidth` and `outerHeight` provide the full width and height of the browser window, including toolbars and scrollbars. This is useful for creating responsive layouts.

```javascript
console.log(window.outerWidth); // Outputs: 1280
console.log(window.outerHeight); // Outputs: 720
```

## 2. Navigation and Opening Windows

The Window object allows for navigation and management of browser windows or tabs. The `location` property represents the current URL and can be used for redirects. The `window.open()` method opens a new window or tab. `window.close()` Closes the current window or tab, used often with windows opened via `window.open()`.

```javascript
window.location.href = "https://www.google.com";
window.open("https://www.google.com");
window.close(); // Closes the current window
```

## 3. Browsing History Manipulation

The Window object allows manipulation of the browser session history, that is the pages visited in the tab or frame, through the `history` object. Methods like `history.back()`, `history.forward()`, and `history.go()` are used to navigate through user's browsing history.

```javascript
window.history.back(); // Goes back one page
window.history.forward(); // Goes forward one page
window.history.go(-2); // Goes back 2 pages
window.history.go(1); // Goes forward 1 page // Goes back two pages
```

## Document Object

The Document object in JavaScript is another crucial concept in web development. It is a part of the Window object and represents the HTML document loaded in a web browser. Through the Document object, you can access and manipulate the content, structure, and styles of a webpage.

When a web page is loaded, the browser creates a Document Object Model (DOM) of the page. The Document object is the entry point to this DOM and allows you to interact with the HTML and CSS of the page.

## 1. DOM Selection Methods

DOM Selection Methods are crucial in web development for accessing and manipulating HTML elements on a webpage. These methods enable you to target specific elements using their unique identifiers, class names, tag names, or even more complex CSS selectors. Understanding these methods is essential for dynamic page manipulation, creating interactive user experiences, and efficiently managing the DOM elements.

## 1.1 Selecting Elements by ID (`getElementById`)

This method selects a single element based on its unique ID. The ID attribute in HTML is meant to be unique, and `getElementById` will return the first element with the specified ID, even if there are multiple elements with the same ID (which is not recommended).

```javascript
let element = document.getElementById("myElement");
```

Ideal for targeting a specific, unique element on the page, such as a specific button, container, or section that has a unique function or style.

**Note:** It will return null if the element is not found and returns single element if it is found.

## 1.2 Selecting Elements by Class Name (`getElementsByClassName`)

This method returns a live HTMLCollection of all elements that have the specified class name. Since classes can be shared among multiple elements, this method can return multiple elements.

```javascript
let elements = document.getElementsByClassName("myClass");
```

Use when you need to select and manipulate a group of elements that share the same class, such as applying a style or event listener to all elements of a particular class.

**Note:** It will return an empty array if the element is not found and returns an HTMLCollection if it is found, which is array-like (but not an actual array) and can be iterated over using loops.

## 1.3 Selecting Elements by Tag Name (`getElementsByTagName`)

This method retrieves all elements with the specified tag name, returning a live HTMLCollection. It's useful for targeting elements by their HTML tag, like <p>, <div>, etc.

```javascript
let elements = document.getElementsByTagName("p");
```

Use when you need to select and manipulate a group of elements that share the same tag name, such as applying a style or event listener to all elements of a particular tag.

**Note:** It will return an empty array if the element is not found and returns an HTMLCollection if it is found, similar to getElementsByClassName.

## 1.4 Selecting Elements by CSS Selector (`querySelector`) and `querySelectorAll`

This method allows you to select elements by their CSS selectors, such as `querySelector` and `querySelectorAll`. It's useful for targeting specific elements based on their CSS class, ID, or tag name.

```javascript
let element = document.querySelector(".myClass"); // Selects the first element with the class "myClass"
let element1 = document.querySelector("#myElement"); // Selects the first element with the ID "myElement"
let element2 = document.querySelector("p"); // Selects the first element with the tag name "p"
let elements = document.querySelectorAll(".myClass"); // Selects all elements with the class "myClass"
```

**Additional Tips**:

`IDs Should Be Unique:` Ensure each element's `ID` is unique to prevent unexpected behavior and maintain valid HTML standards.

`HTMLCollection vs NodeList:` Both are collections of DOM nodes. The key difference is that `NodeList` is static while `HTMLCollection` is live. This means `HTMLCollection` automatically updates when the document changes, while `NodeList` does not.

`Converting Collections to Arrays:` If you need array functionalities for HTMLCollection or NodeList, you can convert them to arrays using `Array.from()`.

## 2. Creating and Modifying Elements in the DOM

JavaScript allows you to dynamically create new HTML elements and add them to your webpage. This is a powerful feature for building interactive and dynamic web pages.

## 2.1 Creating Elements

To start, you use the `document.createElement()` method to create a new element. This element can be customized by setting its `attributes`, applying `styles`, and adding `content`. Finally, the element is inserted into the DOM using methods like `appendChild()`.

Consider a scenario where we have a simple HTML structure with a div element:

```html
<!-- Initial HTML -->
<div id="content"></div>
```

To add a new paragraph to this div:

```javascript
// JavaScript to create and append a paragraph
let newParagraph = document.createElement("p");
newParagraph.textContent = "This is a new paragraph.";
let contentDiv = document.getElementById("content");
contentDiv.appendChild(newParagraph);
```

After this script runs, the HTML will be updated as follows:

```html
<!-- Updated HTML -->
<div id="content">
  <p>This is a new paragraph.</p>
</div>
```

## 2.2 Modifying Elements

Modifying existing elements in the DOM is just as crucial as creating new ones. This can involve changing the `text content`, `updating styles`, `adding classes`, or `setting attributes`. This allows for dynamic updates in response to user actions or other events. For example, to modify a paragraph with a specific ID:

In your HTML

```html
<p id="myParagraph">Initial text content.</p>
```

in your JavaScript

```javascript
let myParagraph = document.getElementById("myParagraph");
myParagraph.textContent = "Updated text content.";
myParagraph.classList.add("highlight");
myParagraph.setAttribute("data-custom", "customValue");
```

This would transform an existing paragraph element in your HTML to include new text, a class, and a custom attribute:

```html
<p id="myParagraph" class="highlight" data-custom="customValue">
  Updated text content.
</p>
```

## 2.3 Removing Elements

Removing elements from the DOM is a critical operation in many dynamic web applications, especially those that need to update the UI in response to user interactions or other changes. To remove an element, you first need to select it, and then you can remove it using the `removeChild()` method from its parent element.

In your HTML

```html
<p id="myParagraph">Initial text content.</p>
```

For instance, to remove a paragraph:

```javascript
let myParagraph = document.getElementById("myParagraph");
let parentElement = myParagraph.parentElement;
parentElement.removeChild(myParagraph);
```

This would result in the removal of the `<p id="myParagraph">` element from its parent in the DOM.

## 3. Styling Elements

Styling elements in the DOM is another crucial aspect of web development. To add, modify, or remove styles, you can use the `style` property of an element.

For example, consider the case where you have an HTML element with a specific ID:

```html
<!-- HTML element to be styled -->
<div id="myElement">Hello, World!</div>
```

To dynamically change the style of this element using JavaScript:

```javascript
// JavaScript for changing styles
let element = document.getElementById("myElement");
element.style.color = "blue"; // Changing text color to blue
element.style.fontSize = "20px"; // Changing font size to 20 pixels
element.style.fontWeight = "bold"; // Making the font bold
```

This script would result in the following changes to the div element:

```html
<!-- Updated HTML -->
<div id="myElement" style="color: blue; font-size: 20px; font-weight: bold;">
  Hello, World!
</div>
```

Manipulating styles through JavaScript offers a dynamic approach to modifying the appearance of web elements, contributing significantly to the interactivity and responsiveness of web applications

## Conclusion

The Document object is a gateway to the web page's content and structure, providing numerous methods for creating, accessing, and manipulating HTML elements. Familiarity with its properties and methods is essential for any front-end developer, as it forms the foundation of interacting with and modifying web page content dynamically.
