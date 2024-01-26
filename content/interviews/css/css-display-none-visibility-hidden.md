+++
title = 'What is the difference between `display:none` and `visibility:hidden` in CSS ?'
date = 2024-01-24T18:41:17+05:30
categories = ["CSS-Interview"]
tags = ["css", "display", "none", "visibility", "hidden", "interview", "css-interview", "css-interview-questions"]
draft = false
weight = 2
+++

### Beginner - Answer 1️⃣

Firstly, `display: none;` and `visibility: hidden;` are both CSS properties used to hide elements on a web page, but they do so in different ways.

In CSS, when you use `display: none`, it's like telling an element to completely disappear from the web page. It's as if the element was never there. On the other hand, visibility: hidden is like making the element invisible, but it still takes up space on the page, just like an invisible box.

### Intermediate - Answer 2️⃣

`display: none` and visibility: hidden are both CSS properties used to hide elements, but they do it differently. When you apply display: none to an element, it removes the element from the document layout. This means the element won't take up any space and it's as if the element is not there at all. However, with visibility: hidden, the element is only made invisible - it's still rendered in the layout and occupies space, but it's just not visible to the user. This distinction is important when you are managing layout and flow of content on your webpage.

### Advanced - Answer 3️⃣

`display: none` and `visibility: hidden` are two CSS properties that both hide elements, but they interact with the document layout and rendering in distinct ways. `display: none` effectively removes the element from the document flow. This means that the element doesn't occupy any space and doesn't affect the positioning of other elements. In contrast, `visibility: hidden` maintains the element in the document layout. The element remains in its place, occupying space and affecting layout, but is not visible. This property's impact is purely visual, without altering the document's box model. This distinction is crucial for nuanced control over document layout and rendering, especially in complex web applications.
