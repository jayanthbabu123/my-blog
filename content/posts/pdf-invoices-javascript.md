+++
title = 'How to create PDF invoices with JavaScript'
date = 2023-12-13T20:19:45+05:30
draft = false
tags = [
  "JavaScript PDF generation",
  "html2pdf library",
  "client-side PDF creation",
  "download PDF invoices",
  "convert HTML to PDF",
  "jsPDF library",
  "html2canvas JavaScript",
  "automate PDF download",
  "PDF generation tutorial",
  "npm html2pdf.js",
  "yarn add html2pdf.js",
  "CDN html2pdf",
  "Bootstrap invoice template",
  "JavaScript invoice download",
  "save PDF from web page",
  "PDF download button",
  "PDF generation from HTML",
  "Hugo site PDF creation",
  "PDF generation JavaScript example",
  "client-side invoice generation",
  "open-source PDF library",
  "PDF generation in browser",
  "HTML to PDF JavaScript",
  "PDF save feature in JavaScript",
  "user-friendly PDF download",
  "PDF generation guide",
  "interactive PDF invoices",
  "PDF download script",
  "HTML invoice to PDF",
  "pdfmake vs html2pdf",
  "frontend PDF generation"
]
categories = ['JavaScript']
favorite= true
image= "/images/pdf-invoices.png"
+++

![How to download web pages as pdf in javascript ](/images/pdf-invoices.png)

### Introduction 🌐

In the digital era, providing users with the option to download data as a PDF is a crucial feature for many websites. PDFs (Portable Document Format) are particularly useful for downloading invoices, ticket bookings, and shopping cart details. This updated guide delves into creating PDFs from HTML using JavaScript, highlighting the html2pdf library, which combines the power of html2canvas and jsPDF for client-side PDF generation.

### Why html2pdf? 🤖

html2pdf offers a versatile solution, converting web pages or elements into printable PDFs entirely on the client side. This approach simplifies the process and enhances user experience by eliminating the need for server-side processing.

### Step-1: Installation 🔧

For modern web development, using package managers like npm or yarn is recommended for a streamlined workflow:

```bash
npm install html2pdf.js
# or
yarn add html2pdf.js

```

Alternatively, you can include the html2pdf CDN link directly in your HTML for simplicity:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>html to pdf</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js"></script>
  </head>
  <body></body>
</html>
```

### Step-2: Creating the Invoice Template 📄

Leveraging Bootstrap for interface styling, we can create a user-friendly and visually appealing invoice template. Here’s an example of how you can structure your HTML for the invoice:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>html to pdf</title>
    <link
      href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css"
      rel="stylesheet"
    />
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js"></script>
  </head>
  <body>
    <div class="container" id="invoice">
      <!-- Sample template code provided in link below -->
    </div>
    <button class="btn btn-primary" id="downloadPdf">Generate Invoice</button>
  </body>
</html>
```

I’ve crafted a sample invoice template, the source code of which is detailed below. Upon interacting with the Generate Invoice button, a script is executed to capture the HTML content and translate it into a downloadable PDF format.

### Step-3: Implementing the PDF Generation Button 🖱️
To initiate the PDF creation, we include a button element in the HTML. This button, when clicked, will trigger the PDF generation process using the html2pdf library:

```html
<button class="btn btn-warning" id="downloadPdf">Generate Invoice</button>
```

In conjunction with the button, we use a JavaScript block to handle the click event. This script captures the HTML content within the invoice container and utilizes html2pdf's methods to generate and save the PDF:

```html
<script>
    document.getElementById('downloadPdf').addEventListener('click', function() {
      const invoiceElement = document.getElementById('invoice');
      const options = {
        margin: 1,
        filename: 'invoice.pdf',
        image: { type: 'jpeg', quality: 0.98 },
        html2canvas: { scale: 2 },
        jsPDF: { unit: 'in', format: 'letter', orientation: 'portrait' }
      };

      // Then call html2pdf with the element and options
      html2pdf().from(invoiceElement).set(options).save();
    });
  </script>

```
### Step-4: Complete Code Snippet for PDF Generation 🛠️
To ensure clarity and provide a hands-on example, here is a complete JavaScript code snippet that demonstrates how to generate a PDF invoice using the html2pdf library. This snippet should be added to your HTML file within a `<script>` tag, just before the closing `</body>` tag.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>html to pdf</title>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet">
  <script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js"></script>
</head>
<body>
  <div class="container" id="invoice">
    <!-- Insert your sample invoice template HTML code here -->
  </div>
  <button class="btn btn-primary" id="downloadPdf">Generate Invoice</button>

  <script>
    document.getElementById('downloadPdf').addEventListener('click', function() {
      const invoiceElement = document.getElementById('invoice');
      const options = {
        margin: 1,
        filename: 'invoice.pdf',
        image: { type: 'jpeg', quality: 0.98 },
        html2canvas: { scale: 2 },
        jsPDF: { unit: 'in', format: 'letter', orientation: 'portrait' }
      };

      // Then call html2pdf with the element and options
      html2pdf().from(invoiceElement).set(options).save();
    });
  </script>
</body>
</html>
```

Make sure to replace the comment `<!-- Insert your sample invoice template HTML code here -->` with your actual invoice template code that you want to be converted into a PDF. This complete snippet now includes the HTML structure, Bootstrap for styling, the html2pdf library for conversion, and the JavaScript necessary to bind the click event to the 'Generate Invoice' button, which upon clicking, will convert the content of the invoice to a downloadable PDF file with the specified options.

### Step-5: Source Code and Live Demonstration 💻
The complete [source code](https://github.com/jayanthbabu123/how-to-convert-html-web-pages-to-pdf-in-javascript) is provided to ensure you can replicate the functionality on your own website. The code includes both the HTML structure and the JavaScript necessary for converting your invoice template into a PDF.

For a practical understanding, a live demo is available that showcases the PDF generation in action. By observing the demo, you can see the exact process and end result of the HTML-to-PDF conversion.

<iframe src="https://codesandbox.io/p/sandbox/html-to-pdf-invoice-javascript-y3lu2" style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;" title="Excel to JSON Demo"></iframe>


### Conclusion ✅
In this guide, we learned how to create PDF invoices using JavaScript and the html2pdf library. This method is great because it’s easy and works directly in the browser, without needing a server. It’s a useful skill for making websites more helpful, especially for things like online shopping receipts or event tickets. By following these steps, you can add this feature to your websites, making them more user-friendly.

Thank you for following along, and happy coding!

