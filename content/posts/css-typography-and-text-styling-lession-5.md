+++
title = 'Typography and Text Styling in CSS - Lession 5'
date = 2024-01-07T20:48:18+05:30
draft = false
categories = ['CSS Learning']
image= "images/typography.webp"
tags = ["css", 
"typography", 
"text styling",
"font family", 
"font size", 
"font weight", 
"font style", 
"text decoration", 
"text transform", 
"text align", 
"line height", 
"letter spacing", 
"word spacing", 
"text indent", 
"text shadow",
]
+++

![Typography and Text Styling in CSS - Lession 5](/images/typography.webp)

### Introduction

Good text styling makes a website more interesting and easier to read. This article will show you how to use CSS, the language for designing web pages, to make your text look great. Whether you're new to web design or looking to brush up on your skills, this guide will help you understand the basics and a bit more about typography and text styling in CSS.

These are the most common and commonly used styles in CSS. We will learn about the following:

- Font Family
- Font Size
- Font Weight
- Font Style
- Text Decoration
- Text Transform
- Text Align
- Line Height
- Letter Spacing
- Word Spacing
- Text Indent
- Text Shadow

Lets discuss each of these in detail

### 1. Font Family

The font-family property in CSS is all about picking the right font for your text. It's like choosing the right outfit for an occasion. You can pick one main font and have a few backups just in case the first one doesn't work.

```css
body {
  font-family: "Calibri", "Arial", sans-serif | "Times New Roman";
}
```

Here, if 'Calibri' isn't available, the browser will try 'Arial', and if that's not there, it will use a default sans-serif font.

### 2. Font Size

The font-size property in CSS is used to set the size of the text. You can use any unit you want. The default font size is `16px`.

```css
body {
  font-size: 16px | 24px | 32px;
}
```

### 3. Font Weight

The font-weight property controls the thickness or boldness of the text. It can be set to values like normal, bold, or numeric values like 400, 700, etc. For example:

```css
body {
  font-weight: bold | normal | 400 | 700 | 900;
}
```

### 4. Font Style

The font-style property controls the style of the text. It can be set to values like normal, italic, or oblique. For example:

```css
div {
  font-style: italic | normal | oblique;
}
```

### 5. Text Decoration

The text-decoration property controls the decoration of the text. It can be set to values like underline, overline, or line-through. For example:

```css
p {
  text-decoration: underline | overline | line-through;
}
```

### 6. Text Transform

The text-transform property controls the case of the text. It can be set to values like uppercase, lowercase, or capitalize. For example:

```css
h1 {
  text-transform: uppercase | lowercase | capitalize;
}
```

### 7. Text Align

The text-align property controls the alignment of the text. It can be set to values like left, right, center, or justify. For example:

```css
p {
  text-align: left | right | center | justify;
}
```

### 8. Line Height

The line-height property controls the spacing between lines of text. It can be set to values like 1, 1.5, or 2. For example:

```css
p {
  line-height: 1 | 1.5 | 2;
}
```

### 9. Letter Spacing

The letter-spacing property controls the spacing between letters. It can be set to values like 0, 0.5, or 1. For example:

```css
p {
  letter-spacing: 0 | 0.5 | 1;
}
```

### 10. Word Spacing

The word-spacing property controls the spacing between words. It can be set to values like 0, 0.5, or 1. For example:

```css
p {
  word-spacing: 0 | 0.5 | 1;
}
```

### 11. Text Indent

The text-indent property controls the indentation of the first line of text. It can be set to values like 0, 1em, or 2em. For example:

```css
p {
  text-indent: 0 | 1em | 2em;
}
```

### 12. Text Shadow

The text-shadow property controls the shadow of the text. It can be set to values like 0 0 5px black, 0 0 10px black, or 0 0 15px black. For example:
`0` is the horizontal offset, `0` is the vertical offset, `5px` is the blur radius, and `black` is the color.

```css
p {
  text-shadow: 0 0 5px black | 0 0 10px black | 0 0 15px black;
}
```

### 13. Word Wrap

The word-wrap property controls the wrapping of the text. It can be set to values like normal, break-word, or nowrap. For example:

```css
p {
  word-wrap: normal | break-word | nowrap;
}
```

```html
<p class="word-wrap">
  This text will be truncated if it overflows its container.
</p>
```

### 14. Text Overflow

The text-overflow property controls the overflow of the text. It can be set to values like clip, ellipsis, or none. For example:

```css
p {
  text-overflow: clip | ellipsis | none;
}
```

The HTML element will be clipped if it overflows its container.

```html
<p class="text-overflow">
  This text will be clipped if it overflows its container.
</p>
```

### Conclusion

Typography and text styling in CSS are key to making websites that are easy to use and look good. By understanding these CSS properties, you can make sure your text does its job well. Remember, the goal is to make your website not just look nice, but also be easy and enjoyable to read. Keep practicing, and you'll be a pro at web typography in no time!

Happy coding! 🚀
