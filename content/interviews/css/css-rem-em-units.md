+++
title = 'What is the difference between "em" and "rem" units in CSS'
date = 2024-01-27T10:41:44+05:30
draft = false
categories = ["CSS-Interview"]
tags = ["css", "rem", "em", "units", "interview", "css-interview", "css-interview-questions"]
weight = 5
+++

### Beginner - Answer 1️⃣

In CSS, `"em"` and `"rem"` are units for measuring sizes, particularly font sizes and layout spacing.

**"em" Unit:** This size is relative to the font size of the parent element. If the parent element's font size is, say, 20px, then 1em for the child element equals 20px. This means the size of an element in "em" changes if the parent's font size changes.

**"rem" Unit:** This is relative to the root element’s font size, often the `<html>` element. If the root font size is 16px, then 1rem equals 16px everywhere on your page, making it consistent across the entire webpage.

### Intermediate - Answer 2️⃣

"em" and "rem" are relative units in CSS, used for responsive and scalable web design.

**"em" Unit:** It equals the font size of its immediate parent element. If an element's parent has a font size of `18px`, then 1em for that element equals `18px`. The size of elements in "em" can change based on the parent's size, which can create cascading effects in nested structures.

**"rem" Unit:** This equals the font size of the root element of the document, typically the `<html>` element. If the root font size is 16px, then 1rem is universally 16px, simplifying the management of global styles and layouts.

### Advanced - Answer 3️⃣

In CSS, "em" and "rem" are scalable units, essential for fluid and responsive web design.

**"em" Unit:** This scales according to the font size of its direct parent element. For example, if a parent element's font size is 15px, then 1em in a child element would be 15px. Its relative nature is effective in component-based design but introduces complexity in deeply nested HTML structures.

**"rem" Unit:** This is relative to the font size of the root element, usually the `<html>` element. If the root font size is set to 16px, then 1rem equals 16px consistently throughout the website. It's advantageous for establishing consistent global typographic and spacing scales, especially in responsive layouts.
