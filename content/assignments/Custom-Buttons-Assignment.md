+++
title = 'Custom CSS Buttons Assignment-5'
date = 2024-01-18T20:20:23+05:30
draft = false
tags = [
    "HTML",
    "CSS",
    "Web Development",
    "HTML Assignments",
    "CSS Assignments",
]
categories = ['HTML', 'CSS']
+++

Create five buttons with distinct styles using HTML and CSS. These buttons will represent common UI elements: primary, success, danger, warning, and info. The buttons should be displayed inline with specific styling for each.
<style>
    .buttons-section {
        margin: 50px auto;
        text-align: center;
    }
    .button {
    padding: 10px 15px;
    border-radius: 5px;
    border: none;
    color: white;
    font-size: 16px;
    margin: 0 5px; 
    cursor: pointer;
    width: 100px;
    transition: background-color 0.3s; 
}

/* Specific button colors */
.primary { background-color: #007bff; }
.success { background-color: #28a745; }
.danger { background-color: #dc3545; }
.warning { background-color: #ffc107; color: black; } /* Override text color for warning button */
.info { background-color: #17a2b8; }

/* Hover effects */
.button:hover {
    opacity: 0.9;
}
</style>
<div class="buttons-section">
<button class="button primary">Primary</button>
<button class="button success">Success</button>
<button class="button danger">Danger</button>
<button class="button warning">Warning</button>
<button class="button info">Info</button>
</div>

## Button Types and Styles

1. **Primary Button**
   - Background Color: `#007bff`
   - Text Color: White
   - Padding: 10px 15px
   - Border: None
2. **Success Button**
   - Background Color: `#28a745`
   - Text Color: White
   - Padding: 10px 15px
   - Border: None
3. **Danger Button**
   - Background Color: `#dc3545`
   - Text Color: White
   - Padding: 10px 15px
   - Border: None
4. **Warning Button**
   - Background Color: `#ffc107`
   - Text Color: Black
   - Padding: 10px 15px
   - Border: None
5. **Info Button**
   - Background Color: `#17a2b8`
   - Text Color: White
   - Padding: 10px 15px
   - Border: None

## Layout Specifications

- Display the buttons inline.
- Ensure there is a margin of 10px between each button.
- The buttons should have a consistent width for uniformity, e.g., `width: 100px`.
- Use a common class for shared styles and individual classes for specific colors.

## HTML Structure

- Use `<button>` or `<input type="button">` elements for the buttons.
- Assign classes to each button to apply the CSS styles.

## CSS Guidelines

- Use class selectors to style the buttons.
- Apply `cursor: pointer;` to change the cursor on hover for better user experience.
- Optionally, add a `:hover` state with a slightly darker background color for interactivity.

## Deliverable

- A static HTML page with five differently styled buttons, as per the above specifications.

---

This assignment aims to enhance your skills in CSS styling and understanding how to use classes effectively for different elements. Focus on creating clean, reusable CSS code and ensuring the buttons are both visually appealing and functional.
