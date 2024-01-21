+++
title = 'Registration Form Design Assignment - 3'
date = 2024-01-18T11:43:26+05:30
draft = false
tags = [
    "HTML",
    "CSS",
    "Web Development",
    "HTML Forms",
    "Registration Form",
    "Form Design",
    "User Interface",
    "User Experience",
    "Form Styling",
    "HTML Assignments",
    "CSS Assignments",
    "HTML Elements",
    "HTML Attributes",
    "HTML Tags",
    "HTML Structure"
]
categories = ['Assignments']

+++

Create an elegant registration form using HTML and CSS. The form should be centered horizontally on the page and include fields for personal information and a submit button. The form should be styled using CSS. This exercise will help you practice form design and CSS styling for user-friendly web forms.

<style>

      .custom-form form {
        background-color: #f4f4f4;
        padding: 2rem;
        border-radius: 8px;
        box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        max-width: 400px;
        margin: auto;
        font-family: Arial, sans-serif;
        width: 100%;
        box-sizing: border-box;
      }

      .custom-form h2 {
        text-align: center;
        color: #333;
        margin-bottom: 1rem;
        margin-top: 0;
      }

      .custom-form .form-group {
        margin-bottom: .7rem;
      }

     .custom-form label {
        display: block;
        margin-bottom: 0.5rem;
        font-weight: bold;
        font-size: 15px;
      }

      .custom-form input[type="text"],
      .custom-form input[type="password"],
      .custom-form input[type="number"],
      .custom-form input[type="date"],
      .custom-form textarea {
        width: 100%;
        padding: 0.75rem;
        border: 1px solid #ccc;
        border-radius: 4px;
        box-sizing: border-box;
        font-size: 15px;
      }


      .custom-form input[type="radio"] {
        margin-right: 0.5rem;
      }

      .custom-form button {
        width: 100%;
        padding: 1rem;
        border: none;
        background-color: #5c6bc0;
        color: white;
        font-size: 1rem;
        border-radius: 4px;
        cursor: pointer;
        transition: background-color 0.3s;
      }

      .custom-form button:hover {
        background-color: #3f51b5;
      }

      .custom-form textarea {
        height: 100px;
      }
</style>
<div class="custom-form">
<form>
      <h2>Register</h2>
      <div class="form-group">
        <label for="first-name">First Name</label>
        <input
          type="text"
          id="first-name"
          placeholder="Enter your first name"
        />
      </div>
      <div class="form-group">
        <label for="last-name">Last Name</label>
        <input type="text" id="last-name" placeholder="Enter your last name" />
      </div>
      <div class="form-group">
        <label for="password">Password</label>
        <input type="password" id="password" placeholder="Create a password" />
      </div>
      <div class="form-group">
        <label for="age">Age</label>
        <input type="number" id="age" placeholder="Enter your age" />
      </div>
      <div class="form-group">
        <label for="dob">Date of Birth</label>
        <input type="date" id="dob" />
      </div>
      <div class="form-group">
        <label>Gender</label>
        <div>
          <input type="radio" name="gender" /> Male
          <input type="radio" name="gender" /> Female
          <input type="radio" name="gender" /> Others
        </div>
        <div></div>
        <div></div>
      </div>
      <div class="form-group">
        <label for="about">About</label>
        <textarea id="about" placeholder="Tell us about yourself"></textarea>
      </div>
      <button type="submit">Submit</button>
    </form>
</div

## Form Requirements:

- **First Name:** A text field for the user's first name.
- **Last Name:** A text field for the user's last name.
- **Password:** Password field for account security.
- **Age:** A number field for the user's age.
- **Date of Birth:** A date picker for the user's date of birth.
- **Gender:** Radio buttons labeled 'Male', 'Female', and 'Other'.
- **About:** A text area for the user to provide additional information.
- **Submit Button:** A button to submit the form.

## Styling Guidelines:

- Use a soft color palette to make the form look inviting and professional.
- Inputs should have subtle `borders` and `padding` to ensure they are comfortable to use.
- Ensure the form has a width as `400px` and is centered on the page.
- Use CSS to style the `labels` and `inputs` consistently and ensure that the form elements are visually aligned.
- The `submit` button should be styled to stand out from the form elements.

## HTML Structure:

- The form should be wrapped in a `<form>` element.
- Use `<input>`, `<textarea>`, and `<button>` elements for the form controls.
- Organize each form control with its label into a logical grouping, potentially using `<div>` or `<fieldset>` elements.

## Deliverable:

Submit a static HTML page with the registration form, as well as a CSS stylesheet.

Make sure that your final design is centered on the page and that each form control is clearly distinguishable. This exercise will help you practice form design and CSS styling for user-friendly web forms.
