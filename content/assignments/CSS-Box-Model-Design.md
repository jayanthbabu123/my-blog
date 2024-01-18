+++
title = 'CSS Box Model Design - Assignment-2'
date = 2024-01-17T21:14:06+05:30
draft = false
tags = [
    "CSS",
    "CSS Box Model",
    "CSS Notes",
    "CSS Tutorial",
    "Web Development",
    "Markup Language",
    "Frontend Development",
    "Web Design",
    "Semantic HTML",
    "Accessibility",
    "Cross-browser Compatibility",
    "Responsive Web Design",
    "Web Accessibility",
    "Best Practices",
    "HTML Elements",
    "HTML Attributes",
    "HTML Tags",
    "HTML Structure",
]
categories = ['CSS']
+++

# Nested Box Layout Assignment

Create a nested box layout using HTML and CSS that visually represents the structure of the box model.

<style>
  .outer-box {
    background-color: #F08080; /* Light Coral */
    padding: 20px;
    max-width: 300px;
    margin: 20px auto;
    box-sizing: border-box;
  }

  .border-box {
    background-color: #AFEEEE; /* Pale Turquoise */
    padding: 20px;
    box-sizing: border-box;
  }

  .padding-box {
    background-color: #98FB98; /* Pale Green */
    padding: 20px;
    box-sizing: border-box;
  }

  .content-box {
    background-color: #87CEEB; /* Sky Blue */
    height: 100px; /* You can adjust the height as needed */
    box-sizing: border-box;
  }
</style>
<div class="outer-box">
  <div class="border-box">
    <div class="padding-box">
      <div class="content-box">
        <!-- Content goes here -->
      </div>
    </div>
  </div>
</div>



## Background Colors:

- **Outermost Box:** Light Coral (`#F08080`)
- **Border Box:** Pale Turquoise (`#AFEEEE`)
- **Padding Box:** Pale Green (`#98FB98`)
- **Content Box:** Sky Blue (`#87CEEB`)

## Required CSS Properties:

- `margin`: Apply to create space around the outermost box.
- `border`: Define on the border box to simulate a border.
- `padding`: Use on the padding box to create space around the content box.
- `background-color`: Assign to each box for visual distinction.
- `width` and `height`: Optionally specify for each box or use default content size.
- `box-sizing`: Set to `border-box` to include padding and border in the element's total width and height.

## HTML Structure:

- Use `<div>` elements nested within each other.

## Deliverable:

A static HTML page with a responsive nested box design that maintains the visual hierarchy on different screen sizes.

---

Ensure that your final design is centered on the page and that each box is clearly distinguishable with the specified background colors. This exercise will help you understand how to use CSS to style elements and manage layout with the box model.
