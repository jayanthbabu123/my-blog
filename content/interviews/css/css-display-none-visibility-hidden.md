+++
title = 'What is the difference between `display:none` and `visibility:hidden` in CSS ?'
date = 2024-01-24T18:41:17+05:30
categories = ["CSS-Interview"]
tags = ["css", "display", "none", "visibility", "hidden", "interview", "css-interview", "css-interview-questions"]
draft = false
weight = 2
+++

Firstly, `display: none;` and `visibility: hidden;` are both CSS properties used to hide elements on a web page, but they do so in different ways.

**1. display: none;** completely removes the element from the document layout. It's like the element was never there. The element does not take up any space, and the space it would have occupied is now available for other elements. Here's a simple

```html
<style>
  .hidden {
    display: none;
  }
</style>

<div>This is visible.</div>
<div class="hidden">This is not visible.</div>
<div>This is also visible.</div>
```

In this example, the second <`div>` is completely removed from the layout. The third `<div>` will take the place where the second `<div>` would have been.

**2. visibility: hidden;** is similar to `display: none;`, except that the element is still present in the layout, but it's hidden from the user. Here's a simple example:

```html
<style>
  .invisible {
    visibility: hidden;
  }
</style>

<div>This is visible.</div>
<div class="invisible">This is invisible but takes up space.</div>
<div>This is visible and pushed down by the invisible div.</div>
```

In this case, the second `<div>` is not visible, but it still occupies space, pushing the third `<div>` down.

In a real-world scenario, choosing between these two depends on your specific needs. If you want to remove an element without affecting the overall layout, go with `display: none;`. But if you need to hide an element temporarily without altering the layout, `visibility: hidden;` is your best bet. It’s all about controlling how elements interact with each other and the space around them in your web design.
