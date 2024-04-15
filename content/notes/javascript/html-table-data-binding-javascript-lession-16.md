+++
title = 'Data Binding in HTML Table using Javascript - Lession 16'
date = 2024-01-30T23:01:13+05:30
draft = false
categories = ['Javascript Learning']
image= "/images/js-table-data-binding.webp"
tags=[
    "Javascript",
    "Javascript Table",
    "Web Development",
    "Frontend Development",
    "Javascript Basics",
    "Javascript Syntax",
    "Javascript Types",
    "Javascript Methods",
    "Table Data Binding",
    "Data Binding",
    "HTML Table"
]
weight = 16
+++

![Data Binding in HTML Table using Javascript - Lession 16](/images/js-table-data-binding.webp)

## Introduction 🌱

Dynamic data binding in JavaScript is a powerful technique for displaying data on a web page. It involves programmatically adding content to the HTML structure, allowing for greater flexibility and interaction with user-generated or external data. This method is particularly useful for rendering data that changes over time or is fetched from a database.

**Example: Displaying Student Data in a Table**

Suppose we have a list of 10 students in a class, represented as an array of objects. Our goal is to dynamically bind this data to an HTML table.

First, let’s define our array of student objects:

```javascript
const students = [
  { name: "John", age: 20, grade: "A" },
  { name: "Jane", age: 21, grade: "B" },
  { name: "Jim", age: 22, grade: "C" },
  { name: "Jen", age: 23, grade: "D" },
  { name: "Jen", age: 24, grade: "E" },
  { name: "Jen", age: 25, grade: "F" },
  { name: "Jen", age: 26, grade: "G" },
  { name: "Jen", age: 27, grade: "H" },
  { name: "Jen", age: 28, grade: "I" },
  { name: "Jen", age: 29, grade: "J" },
];
```

Each student object contains properties like `name`, `age`, and `grade`.

Next, we’ll create a basic HTML structure with a table where our data will be inserted:

```html
<table id="studentTable">
  <thead>
    <tr>
      <th>Name</th>
      <th>Age</th>
      <th>Grade</th>
    </tr>
  </thead>
  <tbody>
    <!-- Dynamic data will be inserted here -->
  </tbody>
</table>
```

Now, we'll write the JavaScript to dynamically insert each student's data into the table:

```javascript
var table = document.getElementById("studentTable");

students.forEach(function (student) {
  var row = table.insertRow();
  var nameCell = row.insertCell(0);
  var ageCell = row.insertCell(1);
  var gradeCell = row.insertCell(2);

  nameCell.textContent = student.name;
  ageCell.textContent = student.age;
  gradeCell.textContent = student.grade;
});
```

- We first get the reference to the table by its ID.
- Then, for each student in our array, we insert a new row into the table.
- For each row, we insert cells corresponding to the student's name, age, and grade.
- Finally, we set the text content of each cell with the respective student's information.

## Approach-2 Using Template Literals

Template literals allow you to embed expressions in string literals, enabling you to create HTML strings with dynamic content more cleanly.

Let’s modify the previous example to use template literals:

Your html will look like this:

```html
<table id="studentTable">
  <tr>
    <th>Name</th>
    <th>Age</th>
    <th>Grade</th>
  </tr>
  <tbody>
    <!-- Dynamic data will be inserted here -->
  </tbody>
</table>
```

```javascript
var students = [
  { name: "John", age: 20, grade: "A" },
  { name: "Jane", age: 21, grade: "B" },
  { name: "Jim", age: 22, grade: "C" },
  { name: "Jen", age: 23, grade: "D" },
  { name: "Jen", age: 24, grade: "E" },
  { name: "Jen", age: 25, grade: "F" },
  { name: "Jen", age: 26, grade: "G" },
  { name: "Jen", age: 27, grade: "H" },
  { name: "Jen", age: 28, grade: "I" },
  { name: "Jen", age: 29, grade: "J" },
];

var tableBody = document
  .getElementById("studentTable")
  .getElementsByTagName("tbody")[0];
var rowsHtml = students
  .map(
    (student) =>
      `<tr>
        <td>${student.name}</td>
        <td>${student.age}</td>
        <td>${student.grade}</td>
    </tr>`
  )
  .join("");

tableBody.innerHTML = rowsHtml;
```

- We first select the `<tbody>` element of our table.
- We then use the map method to transform each student object into a string representing a table row (`<tr>`), with table data (`<td>`) populated using the properties of each student object.
- The `join('')` method combines all these strings into a single HTML string.
- Finally, we set the innerHTML of the table body to this HTML string, effectively populating the table with our student data.

This method is efficient for rendering complex HTML structures with dynamic data. However, it's important to be cautious with innerHTML when dealing with user-provided data, as it can pose a risk for cross-site scripting (XSS) attacks. Always ensure data is properly sanitized before insertion.

## Conclusion

Both methods are effective for dynamically binding data to HTML elements. The choice between them depends on the specific requirements of the project, such as the complexity of the HTML structure and the need for fine-grained control over the DOM manipulation.
