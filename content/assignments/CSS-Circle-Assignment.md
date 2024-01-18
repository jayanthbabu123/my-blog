+++
title = 'Horizontally Centered Circle with Letter - Assignment-4'
date = 2024-01-18T13:08:13+05:30
draft = false
tags = [
    "HTML",
    "CSS",
    "Web Development",
    "CSS Circle Design",
    "HTML Assignments",
    "CSS Assignments",
]
categories = ['HTML', 'CSS']
+++

 <div style="text-align: center;
    background: #e5e5e5;
    padding: 20px;">
 <div class="circle">A</div>
 </div>
 <style>
    .circle {
    width: 100px; /* Circle size */
    height: 100px;
    background-color: #4CAF50; /* Circle background color */
    border-radius: 50%; /* Makes the div circular */
    margin: 0 auto; /* Centers the circle horizontally */
    display: inline-block; /* Necessary for horizontal centering with text-align */
    line-height: 100px; /* Aligns the letter vertically */
    color: white; /* Letter color */
    font-size: 2em; /* Letter size */
    font-family: Arial, sans-serif;
    text-align: center;
}
 </style>

Develop a simple webpage where a circle with a solid background color is horizontally centered, containing a single letter that is centered both horizontally and vertically inside the circle.

## Requirements

- **Circle Design**: Use HTML and CSS to create a circular shape.
- **Horizontal Centering of Circle**: The circle should be centered horizontally on the webpage.
- **Letter Positioning Inside Circle**: Place a single letter (e.g., 'A') inside the circle. This letter should be centered both horizontally and vertically within the circle.
- **Circle Styling**: Choose a distinct background color for the circle, and style the letter to be clearly visible against this background.

## HTML Structure

- Utilize a `<div>` element to create the circle.
- Insert a `<span>` or `<p>` element within the `<div>` for the letter.

## CSS Guidelines

- Ensure the width and height of the circle are equal to form a perfect circle, and use `border-radius` to round it.
- To center the letter inside the circle, use CSS `line-height` and `text-align` to center the letter vertically and horizontally within the circle.
- Apply `margin: 0 auto;` to the circle's container to achieve horizontal centering on the page.

## Deliverable

- A static HTML page that shows the horizontally centered circle with the vertically and horizontally centered letter.

---

This task is aimed at enhancing your skills in CSS positioning, particularly in centering elements. It's a fundamental skill in web design, crucial for creating balanced and visually appealing layouts.
