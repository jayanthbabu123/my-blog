+++
title = 'How to set up JavaScript in Local Environment'
date = 2024-01-08T21:57:00+05:30
draft = false
categories = ['JavaScript-Learning']
image= "/images/javascript-intro.webp"
tags=[
    "JavaScript",
    "JavaScript Setup",
]
weight = 2
+++

![How to set up JavaScript in Local Environment](/images/javascript-intro.webp)

### Introduction

JavaScript is a powerful programming language that can be easily integrated into HTML. Below, you'll find a detailed guide on setting up JavaScript for local development and the two primary methods for including JavaScript scripts in an HTML file.

## Setting Up JavaScript Locally

- **Install a Code Editor:** The first step is to install a text editor for writing your code. Visual Studio Code (VS Code) is a popular choice, known for its rich features and extensions. Download it from Visual Studio Code's website.

- **Create a JavaScript File:** Launch VS Code, create a new file, and save it with a `.js` extension, for example, `script.js`. This is where you'll write your JavaScript code.

- **Write JavaScript Code:** Add your JavaScript code to this file. It can be anything from a simple `console.log('Hello, world!')`.

- **Create an HTML File:** You need an HTML file to run your JavaScript code in a browser. Create a new file and save it with an `.html` extension, such as `index.html`.

### Including JavaScript in HTML

1. **External JavaScript**

External JavaScript involves linking an external .js file to your HTML. This method is preferred for maintaining cleaner code and better organization, especially in larger projects.

In your HTML file, link this JavaScript file using the `<script>` tag. Place the tag in the `<head>` or before the closing `</body>` tag, like so:

```html
<!DOCTYPE html>
<html>
  <head> </head>
  <body>
    <!-- Linking the external JavaScript file -->
    <script src="script.js"></script>
  </body>
</html>
```

2. **Inline JavaScript**

Inline JavaScript involves writing your JavaScript code directly within the `<script>` tag. This method is preferred for simple tasks and for small projects.

In your HTML file, place the JavaScript code between the `<script>` tags.

```html
<!DOCTYPE html>
<html>
  <head> </head>
  <body>
    <!-- Inline JavaScript -->
    <script>
      console.log("Inline JavaScript");
    </script>
  </body>
</html>
```

The browser will execute the JavaScript code within these tags as part of loading the HTML page.

### Conclusion

Setting up and integrating JavaScript into HTML is straightforward and can be done in multiple ways, depending on the project's needs. Whether you opt for external or internal JavaScript, both methods offer flexibility and control in how you deploy your JavaScript code in web environments. 🌐💻🎉
