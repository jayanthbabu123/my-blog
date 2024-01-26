+++
title = 'What is Doctype in HTML 5? Is it mandatory in HTML 5?'
date = 2024-01-19T14:57:06+05:30
draft = false
weight = 2
tags = [
    "HTML",
    "HTML 5",
    "HTML Interview",
    "HTML Notes",
    "HTML Tutorials",
    "HTML Tutorial",
    "HTML Tags",
    "HTML Attributes",
    "HTML Elements",
    "HTML Structure",
    "HTML5",
]
categories = ['HTML Interview']
+++

In HTML5, the DOCTYPE declaration is a way to tell the web browser that, what version and type of HTML the page is written in. Different versions of HTML have different DOCTYPE declarations:

**HTML `4.01`:** The DOCTYPE for HTML `4.01` depends on the type of HTML document you are writing (`Strict`, `Transitional`, or `Frameset`). For example, the Strict DOCTYPE is:

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
```

**HTML5:** The DOCTYPE is simplified in HTML5 and is the same regardless of the type of HTML document:

```html
<!DOCTYPE html>
```

This declaration is a clear signal to the browser that the HTML code that follows is written in HTML5. It's essential because it helps the browser render the content correctly, maintaining consistent behavior across different browsers.

### Is it Mandatory? 🍃

**Technically Optional:** While modern browsers will still render a page without a Doctype, it may not be in HTML 5 standards mode.

**Best Practice:** It is strongly recommended to always include the Doctype in HTML 5 to ensure correct rendering and compatibility across different browsers.

In summary, while Doctype in HTML 5 may not be technically mandatory, it is crucial for ensuring that web pages are rendered correctly and consistently in line with modern web standards.
