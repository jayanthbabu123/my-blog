+++
title = 'How to Convert Excel File Data into a JSON Object Using JavaScript'
date = 2023-12-03T23:44:12+05:30
tags = [
  "JavaScript",
  "Excel",
  "JSON",
  "Data Conversion",
  "Front End Development",
  "Web Development",
  "Programming",
  "XLSX",
  "Client Side Scripting",
  "Code Tutorial"
]
categories = ["JavaScript"]
draft = false
+++

![How Real DOM works with HTML and JavaScript](/images/excel-json-javascript-min.png)
## Introduction 🌐

In today’s fast-paced digital world, efficiency is key, especially when dealing with data. A common challenge many developers face is converting `Excel files` into `JSON` format for easier manipulation and integration into web applications. While there are various methods to achieve this, using JavaScript for client-side conversion stands out for its simplicity and effectiveness. This approach negates the need for server-side processing, offering a swift and streamlined solution directly in the browser.

In this comprehensive guide, we’ll explore how to transform `Excel data` into `JSON` objects using pure JavaScript. We’ll dive into the JavaScript library `XLSX`, a powerful tool for reading Excel files and converting them to `JSON`. This tutorial is perfect for developers looking to enhance their front-end development skills, offering a straightforward method to handle Excel files in web applications. Whether you’re a beginner or a seasoned coder, you’ll find valuable insights on leveraging JavaScript for Excel to JSON conversion, improving data handling in your projects.

The conversion process utilizes a JavaScript plugin named `XLSX`, which is adept at interpreting Excel files as binary strings and subsequently transforming them into JSON objects.

**Plugins Required:** xlsx.full.min.js

## Step-1: Setting Up the XLSX Library ⚙️

Begin by incorporating the `XLSX` library into your HTML document. This is done by adding the `CDN (Content Delivery Network) link` of the library within the `<head>` tag of your HTML file, as shown below:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Document</title>
    <script
      type="text/javascript"
      src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.15.3/xlsx.full.min.js"
    ></script>
  </head>

  <body></body>
</html>
```

## Step-2: Creating the File Input and Convert Button 📂

Now, within the `<body>` section of your HTML document, we need to insert an `<input>` element configured to accept files. Specifically, we want to ensure that users can only select files with an `.xls` or `.xlsx` extension, which are standard formats for Excel files. Insert the following code snippet into the `<body>` tag of your HTML to achieve this:

```html
<input type="file" id="fileUpload" accept=".xls,.xlsx" />
<br />
<button type="button" id="uploadExcel">Convert</button>
<pre id="jsonData"></pre>
```

This code creates a file input field that filters out non-Excel files, a button that initiates the conversion process, and a `<pre>` element to display the formatted JSON output after conversion.

## Step-3: Implementing Event Listeners in JavaScript 🔊
 
Now we need to add event listeners for both the input and button elements to handle changes in the input and button click events. In JavaScript, event listeners are functions that wait for an event to occur, like a file being selected or a button being clicked. Here’s how we can add them to our elements:

```javascript
document.getElementById("fileUpload").addEventListener("change", (event) => {
  // This event listener monitors the file input for changes, indicating that a file has been selected.
});

document.getElementById("uploadExcel").addEventListener("click", () => {
  // This event listener waits for the 'Convert' button to be clicked to start the conversion process.
});
```

### Step-4: The Conversion Logic 🧮

In JavaScript, we can read the contents of an Excel file by utilizing the FileReader object to process the file's data as a binary string. Once we have the binary representation of the file, we leverage the capabilities of the XLSX library, which utilizes SheetJS under the hood, to parse this binary string and convert it into a JSON object. The XLSX library simplifies the process of translating Excel's cell-based structure into a JavaScript-friendly JSON format, making the data ready for use within our web applications.

Here’s the complete HTML and JavaScript code that encapsulates the entire conversion process.

``` html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Document</title>
    <script
      type="text/javascript"
      src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.15.3/xlsx.full.min.js"
    ></script>
  </head>

  <body>
    <input type="file" id="fileUpload" accept=".xls,.xlsx" /><br />
    <button type="button" id="uploadExcel">Convert</button>
    <pre id="jsonData"></pre>
  </body>
  <script>
    var selectedFile;
    document
      .getElementById("fileUpload")
      .addEventListener("change", function (event) {
        selectedFile = event.target.files[0];
      });

    document
      .getElementById("uploadExcel")
      .addEventListener("click", function () {
        if (selectedFile) {
          console.log("hi");
          var fileReader = new FileReader();
          fileReader.onload = function (event) {
            var data = event.target.result;

            var workbook = XLSX.read(data, {
              type: "binary",
            });
            workbook.SheetNames.forEach((sheet) => {
              let rowObject = XLSX.utils.sheet_to_row_object_array(
                workbook.Sheets[sheet]
              );
              let jsonObject = JSON.stringify(rowObject);
              document.getElementById("jsonData").innerHTML = jsonObject;
              console.log(jsonObject);
            });
          };
          fileReader.readAsBinaryString(selectedFile);
        }
      });
  </script>
</html>
```

### Step-5: Execution and Output 🚀
Choose the desired Excel file by clicking on the file selection field, then press the `Convert` button. This action triggers the conversion process, and the resulting JSON object will be displayed directly within the browser. You can then employ this JSON data for various tasks, such as manipulating its content or seamlessly integrating it into diverse user interface layouts.

To facilitate your understanding, I’ve included a live `demo` via a `CodeSandbox` link below. For direct access to the source code, click on the following link.

Click here for source code [source code](https://github.com/jayanthbabu123/excel-to-json-by-javascript)

<iframe src="https://codesandbox.io/p/sandbox/excel-to-json-object-t4lbf" style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;" title="Excel to JSON Demo"></iframe>

### Additional Resources
For those interested in converting Excel files to JSON using Angular, please refer to the following video tutorial for guidance:

<iframe width="680" height="382" src="https://www.youtube.com/embed/iT_l0l-SPDY" title="How to Convert Excel file into JSON by using Angular | JavaScript | JSON" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

If you’re looking to export a JSON object to an Excel format, consider watching this instructional video for assistance:

<iframe width="680" height="382" src="https://www.youtube.com/embed/AaN9riXBMTw" title="How to export as excel from JSON object by using JavaScript | JavaScript Tutorials" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

### Conclusion 📚
In this guide, we’ve walked through the process of converting Excel files to JSON using JavaScript. This skill is invaluable in modern web development and can be applied to a range of projects.

👏 Appreciate your attention. Thank you! :)
