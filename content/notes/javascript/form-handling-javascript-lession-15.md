+++
title = 'Form Handling in Javascript - Lession 15'
date = 2024-01-30T22:45:03+05:30
draft = false
categories = ['Javascript Learning']
image= "/images/js-form.webp"
tags=[
    "Javascript",
    "Javascript Form",
    "Web Development",
    "Frontend Development",
    "Javascript Basics",
    "Javascript Syntax",
    "Javascript Types",
    "Javascript Methods",
    "Form Handling"
]
weight = 15
+++

![Form Handling in Javascript - Lession 15](/images/js-form.webp)

## Introduction 🌱

Form handling is a critical aspect of web development, allowing developers to capture user input and process it effectively. JavaScript plays a key role in managing forms, enabling validation, gathering data, and controlling form submission.

In this guide, we will explore how to handle form data in JavaScript. We'll create an example form with fields like username, email, password, and gender (using radio buttons). Upon submission, we'll capture the input data and display it in a structured JSON format below the form.

**Creating the Form**

Our form will include various input types: text for username, email, password, and radio buttons for gender selection. We'll also have a submit button to trigger data capture.

```html
<form id="userForm">
  <label for="username">Username:</label>
  <input type="text" id="username" name="username" required /><br />

  <label for="email">Email:</label>
  <input type="email" id="email" name="email" required /><br />

  <label for="password">Password:</label>
  <input type="password" id="password" name="password" required /><br />

  <label>Gender:</label>
  <input type="radio" id="male" name="gender" value="male" />
  <label for="male">Male</label>
  <input type="radio" id="female" name="gender" value="female" />
  <label for="female">Female</label><br />

  <button type="submit">Submit</button>
</form>

<pre id="result"></pre>
```

**Handling the Form Submission**

To handle the form submission, we'll add an event listener to the form for the submit event. When the form is submitted, we'll prevent the default submission action, gather the data from each form field, and then display this data as JSON.

```javascript
const form = document.getElementById("userForm");
form.addEventListener("submit", (event) => {
  event.preventDefault();
  const username = document.getElementById("username").value;
  const email = document.getElementById("email").value;
  const password = document.getElementById("password").value;
  const gender = document.querySelector('input[name="gender"]:checked').value;
  const result = document.getElementById("result");
  const data = { username, email, password, gender };
  result.textContent = JSON.stringify(data);
});
```

- We use document.getElementById to access the form and input elements.
- event.preventDefault() stops the default form submission behavior, which normally reloads the page.
- We gather data from each input field. For the gender radio buttons, we use document.querySelector to select the checked radio button.
- Finally, we display the captured data as a JSON string in the `<pre>` tag.

## Approach-2 with FormData

`FormData` provides a simpler and more straightforward approach to handling forms in JavaScript. It's an API that allows you to easily construct a set of key/value pairs representing form fields and their values, which can be sent using `XMLHttpRequest` or used for other processing needs. This method is particularly useful for handling complex forms and can be more efficient than manually retrieving each field's value.

**Building the Form**

Let's create a form similar to the previous example, including fields for username, email, password, and gender radio buttons.

```html
<form id="userForm">
  <label for="username">Username:</label>
  <input type="text" id="username" name="username" required /><br />

  <label for="email">Email:</label>
  <input type="email" id="email" name="email" required /><br />

  <label for="password">Password:</label>
  <input type="password" id="password" name="password" required /><br />

  <label>Gender:</label>
  <input type="radio" id="male" name="gender" value="male" />
  <label for="male">Male</label>
  <input type="radio" id="female" name="gender" value="female" />
  <label for="female">Female</label><br />

  <button type="submit">Submit</button>
</form>

<pre id="result"></pre>
```

To handle the form submission using FormData, we'll add an event listener to the form. When the form is submitted, FormData will automatically capture all the form data.

```javascript
document
  .getElementById("userForm")
  .addEventListener("submit", function (event) {
    event.preventDefault(); // Prevents the default form submission
    // const form = document.getElementById("userForm");
    // var formData = new FormData(form);
    var formData = new FormData(this); // 'this' refers to the form element
    var object = {};
    formData.forEach(function (value, key) {
      object[key] = value;
    });

    var jsonData = JSON.stringify(object);
    document.getElementById("result").textContent = jsonData;
  });
```

- We create a new instance of FormData, passing the form as an argument.
- The forEach method of FormData is used to iterate over all form fields, constructing an object where each key corresponds to a form field's name, and each value corresponds to the user's input.
- This object is then converted to a JSON string using JSON.stringify and displayed in the `<pre>` tag.

FormData in JavaScript offers a streamlined, efficient approach to form handling, reducing the need for manual data collection and simplifying the process of working with user input. It's particularly beneficial in scenarios involving complex forms or when integrating with AJAX for asynchronous data submission. This method enhances the usability and maintainability of form-related code in web applications.

## Conclusion on Form Handling

**Manual Data Collection:** Involves individually accessing each form element to gather data. This method offers granular control over each input field but can be more verbose, especially for complex forms.

**Using FormData:** Streamlines form handling by automatically capturing form data, reducing code complexity and enhancing efficiency. Ideal for handling complex forms and integrating with AJAX, but offers less control over individual form elements compared to manual methods.

Both approaches have their unique advantages, and the choice largely depends on the specific requirements and complexity of the form being handled in the web application.
