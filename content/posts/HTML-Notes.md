+++
title = 'Complete HTML Guide'
date = 2023-12-28T23:01:38+05:30
draft = false
tags = [
    "HTML",
    "HTML5",
    "HTML Guide",
    "HTML Notes",
    "HTML Tutorial",
    "Web Development",
    "Markup Language",
    "Frontend Development",
    "Web Design",
    "Semantic HTML",
    "SEO",
    "Accessibility",
    "Cross-browser Compatibility",
    "Responsive Web Design",
    "Web Accessibility",
    "Best Practices",
    "HTML Elements",
    "HTML Attributes",
    "HTML Tags",
    "HTML Structure",
    "HTML Formatting",
    "HTML Semantics",
    "HTML Forms",
    "HTML Tables",
    "HTML Images",
    "HTML Links",
    "HTML Headings",
    "HTML Lists",
    "HTML Media",
    "HTML Layout",
    "HTML Metadata",
    "HTML Doctype",
    "HTML Validation",
    "HTML Standards"
]
categories = ['HTML']
image= "https://i.postimg.cc/FRNDTRQw/html-guide.png"

+++

![HTML Notes](https://i.postimg.cc/FRNDTRQw/html-guide.png)

**What is HTML?**

HTML (Hypertext Markup Language) is the standard markup language used for creating web pages and web applications. It is not a programming language but a markup language that defines the structure of your content.

The current version of HTML is HTML5, officially released in October 2014.

HTML is the standard language for creating web pages, serving as the foundational building block for web content. It provides the essential structure and layout for web pages, which is then enhanced and styled by CSS and made interactive with JavaScript.

### Setting Up a Basic HTML File

I don't recommend the traditional Notepad approach for creating HTML files. It's too basic and lacks the features needed for efficient web development.

- **Step-1: Install Visual Studio Code:**
  Start by installing Visual Studio Code (VS Code). It's a powerful and popular code editor that offers many features beneficial for web development.

- **Step-2: Create a Project Folder:** On your computer, choose a convenient location like your desktop, and create a new folder. Name it something like 'html-practice' to signify its purpose.

- **Step-3: Open the Folder in VS Code:** Launch Visual Studio Code and open the 'html-practice' folder. This step is crucial as it helps you organize your work and use the powerful features of VS Code.

- **Step-4: Create an HTML File:** Inside the 'html-practice' folder, create a new file. Name it with an .html extension, such as index.html. This is your HTML file where you will write your HTML code.

- **Step-5: Open the HTML File in VS Code:** Open the 'index.html' file in VS Code. You can now start writing your HTML code in the editor.

- **Step-6: Start Coding:** Now, with your index.html file open in VS Code, you can start writing your HTML code. VS Code will provide syntax highlighting and other helpful tools to make your coding more efficient.

- **Step-7: Preview Your Web Page:** As you write your HTML code, it's important to frequently preview your web page. In Visual Studio Code, you can use extensions like "Live Server" to view your web page in real-time. This tool automatically refreshes the page in your browser whenever you save changes, allowing you to immediately see the impact of your code.

### HTML Structure

Understanding the structure of an HTML document is crucial for effective web development. Every HTML page begins with a DOCTYPE declaration, which is essential in informing the web browser about the version of HTML the page is written in. Over the years, as HTML has evolved, the DOCTYPE has changed to reflect different versions. In HTML5, the latest version, the DOCTYPE declaration is simplified to:

```html
<!DOCTYPE html>
```

This line must be placed at the very top of your HTML document. It is a declaration rather than a tag, and it ensures that your HTML code is interpreted correctly by different browsers.

Following the DOCTYPE declaration, an HTML document is structured into two main sections: the `<head>` and the `<body>`.

1. The Head Section (`<head>`): This part of the document contains meta-information about the document, which isn't displayed directly on the web page. It includes elements such as the title of the document, links to stylesheets, meta tags for SEO, and scripts. The `<title>` tag within the head is particularly important as it defines the title of the web page, which appears in the browser's title bar or tab.

2. The Body Section (`<body>`): This is where the content that will be displayed to users on the webpage is placed. It can contain various elements like headings, paragraphs, images, links, lists, and more. Essentially, whatever you want to show to the users on your webpage will be a part of the `<body>`.

Here's a basic example of an HTML5 document structure:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>My Webpage</title>
  </head>
  <body>
    <h1>Welcome to My Webpage</h1>
    <p>This is my first webpage!</p>
  </body>
</html>
```

In this structure, `<html>` acts as the root element that encapsulates the entire content of the web page. It's important to remember that while the `<head>` section contains information about the document, the `<body>` section contains the actual content that will be visible to your web page visitors.

### Head Tag and Elements Inside of It

The `<head>` tag in HTML serves as a container for meta-information about the document. It contains essential elements that provide information to the browser and search engines, but these elements do not directly display content on the web page itself. Let's explore the common elements that can be placed within the `<head>` tag, along with example code snippets and explanations:

1. **Title (`<title>`)**
   The `<title>` element defines the title of the web page, which is displayed in the browser's title bar or tab. It's a crucial element for both user experience and SEO.

```html
<head>
  <title>My Website</title>
</head>
```

In this example, the title of the web page is "My Website".

2. **Meta Tags (`<meta>`)**
   Meta tags provide metadata about the HTML document. Commonly used meta tags include character set declaration, viewport settings, and descriptions for search engines.

```html
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta
    name="description"
    content="A description of your webpage for search engines"
  />
</head>
```

3. **Link to Stylesheets (`<link>`)**
   The `<link>` element is used to link external resources, such as stylesheets, to the HTML document. It's commonly used for applying CSS styles to the page.

```html
<head>
  <link rel="stylesheet" href="style.css" />
</head>
```

4. **Scripts (`<script>`)**
   The `<script>` element is used to add JavaScript code to the HTML document. It can be used for client-side processing, such as form validation, data manipulation, and more.

```html
<head>
  <script src="script.js"></script>
</head>
```

5. **Favicon (`<link>`)**
   The `<link>` element can be used to specify a favicon for your website. You typically provide the path to the favicon image using the rel attribute set to "icon".

```html
<head>
  <title>My Website</title>
  <!-- Other head elements as needed -->
  <link rel="icon" href="favicon.ico" type="image/x-icon" />
</head>
```

In this example, the href attribute points to the location of the favicon file (favicon.ico). The type attribute specifies the file type, which is usually "image/x-icon" for favicon files.

Here's the complete HTML structure including the favicon:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>My Website</title>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta
      name="description"
      content="A description of your webpage for search engines"
    />
    <link rel="stylesheet" href="styles.css" />
    <script src="script.js"></script>
    <link rel="icon" href="favicon.ico" type="image/x-icon" />
    <!-- You can add more meta tags, links, or scripts as needed -->
  </head>
  <body>
    <!-- Content of your webpage goes here -->
  </body>
</html>
```

### Body Tag and Elements Inside of It

The `<body>` tag in HTML is where the main content of a web page is placed. It defines what users see and interact with when they visit your website. The content inside the `<body>` tag can be divided into two main types of elements: `block-level` elements and `inline` elements.

### Block-Level Elements

Block-level elements are HTML elements that create a "block" of content. Each block-level element typically starts on a new line and stretches the full width of its parent container (usually the `<body>` or another block-level element). Block-level elements are used to structure the layout and hierarchy of a web page. Let's explore some common block-level elements in detail with code snippets:

- **Headings (`<h1>`, `<h2>`, `<h3>`,`<h4>`, `<h5>`, `<h6>`)**

  Headings define the hierarchical structure of your content, with `<h1>` being the highest level and `<h6>` the lowest. They are used to create titles and subtitles for different sections of your web page.

  ```html
  <h1>Main Heading</h1>
  <h2>Subheading</h2>
  <h3>Sub-subheading</h3>
  <h4>Sub-sub-subheading</h4>
  <h5>Sub-sub-sub-subheading</h5>
  <h6>Sub-sub-sub-sub-subheading</h6>
  ```

- **Paragraphs (`<p>`)**

  Paragraphs are used to structure text into logical units. They create space before and after the content, making it visually distinct.

  ```html
  <p>This is a paragraph.</p>
  <p>This is another paragraph.</p>
  ```

- **Divisions (`<div>`)**

  The `<div>` element is a generic container used for grouping and styling content. It doesn't add any specific visual styling by itself but is a versatile building block for layout design.

  ```html
  <div class="container">
    <p>Content within a div.</p>
  </div>
  ```

- **Lists (`<ul>`, `<ol>`, `<li>`)**
  Lists are used to organize and display information in a specific order. They can be created with the `<ul>` element for unordered lists, `<ol>` for ordered lists, and `<li>` for list items.

  ```html
  <ul>
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
  </ul>

  <ol>
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
  </ol>
  ```

- **Horizontal Rule (`<hr>`)**

  The `<hr>` element creates a horizontal line or thematic break, often used to separate content.

  ```html
  <hr />
  ```

- **Semantic Elements (`<article>`, `<section>`, `<nav>`, `<header>`, `<footer>`, etc.)**

  HTML5 introduced a set of semantic elements that provide meaning to the structure of a webpage. These elements help define the roles of different sections of a page.

  ```html
  <article>
    <h2>Article Title</h2>
    <p>Content of the article.</p>
  </article>

  <section>
    <h2>Section Title</h2>
    <p>Content of the section.</p>
  </section>

  <nav>
    <!-- Navigation links -->
  </nav>

  <header>
    <!-- Header content -->
  </header>

  <footer>
    <!-- Footer content -->
  </footer>
  ```

- **BlockQuote (`<blockquote>`)**

  The `<blockquote>` element is used to create a blockquote element. It is used to quote a section of text from another source.

  ```html
  <blockquote>"This is a blockquote."</blockquote>
  ```

- **Tables (`<table>`, `<tr>`, `<td>`, `<th>`, etc.)**

  Tables are used to organize and display data in a tabular format. They can be created with the `<table>` element, `<tr>` for table rows, `<td>` for table cells, and `<th>` for table headers.

  ```html
  <table>
    <tr>
      <th>Column 1</th>
      <th>Column 2</th>
    </tr>
    <tr>
      <td>Row 1, Column 1</td>
      <td>Row 1, Column 2</td>
    </tr>
    <tr>
      <td>Row 2, Column 1</td>
      <td>Row 2, Column 2</td>
    </tr>
  </table>
  ```

### Inline Elements

Inline elements in HTML are used within the content of block-level elements to apply specific styles or create inline-level structures. Unlike block-level elements, inline elements do not create new "blocks" of content and do not start on new lines. Instead, they flow within the text or content of block-level elements. Let's explore some common inline elements in detail with code snippets:

- span (`<span>`)

  The `<span>` element is used to group inline content. It is used to apply styles to a part of the text.

  ```html
  <span style="color: red;">This text is red.</span>
  ```

- **Link (`<a>`)**

  The `<a>` element is used to create hyperlinks, allowing users to navigate to other web pages or resources. It has an href attribute that specifies the URL to link to.

  ```html
  <a href="https://example.com">Link</a>
  ```

- **Image (`<img>`)**

  The `<img>` element is used to embed an image in an HTML document. It has an src attribute that specifies the source URL of the image.

  ```html
  <img src="image.jpg" alt="Image" />
  ```

- **Text Styling (`<em>`, `<i>`, `<b>`, `<strong>`)**

  Text styling elements, such as `<em>`, `<i>`, `<b>`, and `<strong>`, are used to apply emphasis, italicization, boldface, and strong emphasis to the text.

  ```html
  <p><em>This text is italic.</em></p>
  <p><i>This text is italic.</i></p>
  <p><b>This text is bold.</b></p>
  <p><strong>This text is bold.</strong></p>
  ```

- **Abbreviations (`<abbr>`) and Definitions (`<dfn>`)**

  `<abbr>` is used for abbreviations or acronyms, and `<dfn>` is used for defining terms.

  ```html
  <p>
    <abbr title="HyperText Markup Language">HTML</abbr> is the standard markup
    language for creating web pages.
  </p>
  <p>
    <dfn>HyperText Markup Language</dfn> is the standard markup language for
    creating web pages.
  </p>
  ```

- **input (`<input>`)**

  The `<input>` element is used to create interactive controls, such as text fields, checkboxes, and radio buttons. It has an input type attribute that specifies the type of control.

  ```html
  <input type="text" />
  <input type="checkbox" />
  <input type="radio" />
  ```

  The `<input>` element is a versatile inline element used extensively in web forms for user interaction and data submission.

- **button (`<button>`)**

  The `<button>` element is used to create interactive controls, such as buttons, checkboxes, and radio buttons. It has an input type attribute that specifies the type of control.

  ```html
  <button type="button">Button</button>
  <button type="submit">Submit</button>
  <button type="reset">Reset</button>
  ```

### Forms

Forms in HTML are used to collect and submit user input. They allow users to enter data, make selections, and interact with a website. Here's an explanation of forms with code snippets and examples:

- **Form (`<form>`)**

  The `<form>` element is used to create a form on a web page. It acts as a container for form controls like text fields, checkboxes, and buttons. The action attribute specifies the URL where the form data will be sent when submitted, and the method attribute defines the HTTP method (usually GET or POST).

  ```html
  <form action="submit.php" method="post">
    <label for="name">Name:</label>
    <input type="text" id="name" name="name" />
    <button type="submit">Submit</button>
  </form>
  ```

- **Text Fields (`<input type="text">`)**

  The `<input type="text">` element is used to create text fields in a form. It has an id and name attributes that allow the form data to be uniquely identified.

  ```html
  <input type="text" id="name" name="name" />
  ```

- **Text Areas (`<textarea>`)**

  Text areas are used for multiline text input. The `<textarea>` element defines a textarea where users can enter longer text, such as comments or messages.

  ```html
  <label for="message">Message:</label>
  <textarea id="message" name="message" rows="4" cols="50"></textarea>
  ```

- **Checkboxes (`<input type="checkbox">`)**
  Checkboxes allow users to select one or more options from a list. The `<input>` element with type="checkbox" creates a checkbox input.

  ```html
  <input type="checkbox" id="vehicle1" name="vehicle1" value="Bike" />
  <label for="vehicle1">I have a bike</label><br />
  <input type="checkbox" id="vehicle2" name="vehicle2" value="Car" />
  <label for="vehicle2">I have a car</label><br />
  <input type="checkbox" id="vehicle3" name="vehicle3" value="Boat" />
  <label for="vehicle3">I have a boat</label>
  ```

- **Radio Buttons (`<input type="radio">`)**

  Radio buttons allow users to select one option from a list. The `<input>` element with type="radio" creates a radio button input. Radio buttons within the same name attribute group allow only one selection.

  ```html
  <input type="radio" id="male" name="gender" value="male" />
  <label for="male">Male</label><br />
  <input type="radio" id="female" name="gender" value="female" />
  <label for="female">Female</label><br />
  <input type="radio" id="other" name="gender" value="other" />
  <label for="other">Other</label>
  ```

- **Dropdown Lists (`<select>`)**

  Dropdown lists, also known as select elements, allow users to select one option from a list of options. The `<select>` element creates the dropdown, and `<option>` elements define the individual options.

  ```html
  <label for="cars">Choose a car:</label>
  <select id="cars" name="cars">
    <option value="volvo">Volvo</option>
    <option value="saab">Saab</option>
    <option value="fiat">Fiat</option>
    <option value="audi">Audi</option>
  </select>
  ```

  <label for="cars">Choose a car:</label>
  <select id="cars" name="cars">
    <option value="volvo">Volvo</option>
    <option value="saab">Saab</option>
    <option value="fiat">Fiat</option>
    <option value="audi">Audi</option>
  </select>

- **Buttons (`<button>`)**

  Buttons can be used to submit the form, reset form fields, or trigger custom JavaScript functions. The `<button>` element can have different type attributes, such as "submit," "reset," or "button."

  ```html
  <button type="submit">Submit</button>
  <button type="reset">Reset</button>
  <button type="button" onclick="myFunction()">Click me</button>
  ```

- **Form Labels (`<label>`)**
  Labels (`<label>`) are used to provide a textual description for form elements, improving accessibility and user experience. They are associated with form controls using the for attribute.

  ```html
  <label for="name">Name:</label> <input type="text" id="name" name="name" />
  ```

  HTML forms are essential for interactive web applications and data collection. They allow users to input and submit data, making them a fundamental part of web development.

### Table

Tables in HTML are used to organize and display data in a structured format. They consist of rows and columns, with each cell holding data or other HTML elements. Here's an explanation of tables with code snippets and examples:

- **Table Structure (`<table>`)**

  The `<table>` element is used to create a table on a web page. Tables are divided into rows (`<tr>`) and columns (`<th>` for headers and `<td>` for data cells).

  ```html
  <table>
    <tr>
      <th>Header 1</th>
      <th>Header 2</th>
    </tr>
    <tr>
      <td>Data 1</td>
      <td>Data 2</td>
    </tr>
  </table>
  ```

- **Table Headers (`<th>`)**

  The `<th>` element is used to define header cells in a table. These cells are typically bold and centered. They provide labels for columns or rows.

  ```html
  <table>
    <tr>
      <th>Name</th>
      <th>Age</th>
      <th>Country</th>
    </tr>
    <tr>
      <td>John</td>
      <td>25</td>
      <td>USA</td>
    </tr>
  </table>
  ```

- **Table Data (`<td>`)**

  The `<td>` element is used to define data cells in a table. These cells contain data or other HTML elements. They display data in rows and columns.

  ```html
  <table>
    <tr>
      <td>Name</td>
      <td>Age</td>
      <td>Country</td>
    </tr>
    <tr>
      <td>John</td>
      <td>25</td>
      <td>USA</td>
    </tr>
  </table>
  ```

- **Table Caption (`<caption>`)**

  The `<caption>` element is used to define the caption of a table. It is typically used to provide additional information about the table.

  ```html
  <table>
    <caption>
      Table Caption
    </caption>
    <tr>
      <th>Name</th>
      <th>Age</th>
      <th>Country</th>
    </tr>
    <tr>
      <td>John</td>
      <td>25</td>
      <td>USA</td>
    </tr>
  </table>
  ```

- **Table Row Grouping (`<tbody>`, `<thead>`, `<tfoot>`)**

  Large tables can be divided into header, body, and footer sections using these elements. The `<thead>` element contains header rows, the `<tbody>` element contains data rows, and the `<tfoot>` element contains footer rows.

  ```html
  <table>
    <thead>
      <tr>
        <th>Name</th>
        <th>Age</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>John</td>
        <td>25</td>
      </tr>
      <tr>
        <td>Lisa</td>
        <td>30</td>
      </tr>
    </tbody>
    <tfoot>
      <tr>
        <td colspan="2">Total: 2 employees</td>
      </tr>
    </tfoot>
  </table>
  ```

  Tables are commonly used for presenting data, such as lists of items, financial reports, or other structured information. They provide an organized way to display data in rows and columns, making it easier for users to understand and compare information.

### Media Elements

Media elements in HTML allow you to embed and display various types of media content, such as images, audio, and video, on a web page. Here's an explanation of media elements with code snippets and examples:

- **Image (`<img>`)**

  Images are commonly used in web pages to display graphics, photos, icons, and more. The `<img>` element is used to embed images in HTML.

  ```html
  <img
    src="image.jpg"
    alt="Description of the image"
    width="300"
    height="200"
  />
  ```

  - src: Specifies the source URL of the image.
  - alt: Provides alternative text for the image (useful for accessibility).
  - width and height: Define the dimensions of the image.

- **Audio (`<audio>`)**
  The `<audio>` element is used to embed audio files on a web page. It supports various audio formats such as MP3, WAV, and OGG.

  ```html
  <audio controls>
    <source src="audio.mp3" type="audio/mpeg" />
    Your browser does not support the audio element.
  </audio>
  ```

  - controls: Adds audio controls (play, pause, volume) to the player.
  - `<source>`: Specifies the audio source and type.

- **Video (`<video>`)**

  The `<video>` element is used to embed video files on a web page. It supports various video formats such as MP4, WebM, and OGG.

  ```html
  <video controls width="400" height="300">
    <source src="video.mp4" type="video/mp4" />
    Your browser does not support the video element.
  </video>
  ```

  - controls: Adds video controls (play, pause, volume, fullscreen) to the player.
  - width and height: Define the dimensions of the video player.
  - `<source>`: Specifies the video source and type.

- **Embedded Content (`<iframe>`)**

  The `<iframe>` element allows you to embed external content, such as maps, social media posts, or external web pages, within your HTML document.

  ```html
  <iframe
    src="https://www.youtube.com/embed/video_id"
    width="560"
    height="315"
    frameborder="0"
    allowfullscreen
  ></iframe>
  ```

  - **src:** Specifies the URL of the external content.
  - **width and height:** Define the dimensions of the embedded content.
  - **frameborder:** Adds a border around the embedded content.
  - **allowfullscreen:** Enables fullscreen mode for the embedded content.

- **Responsive Images**

  To ensure that images are responsive and adapt to different screen sizes, you can use CSS or the srcset attribute to provide multiple image sources with different resolutions.

  ```html
  <img
    src="image.jpg"
    alt="Description of the image"
    srcset="image-320w.jpg 320w, image-480w.jpg 480w, image-800w.jpg 800w"
    sizes="(max-width: 320px) 280px,
            (max-width: 480px) 440px,
            800px"
  />
  ```

  - **src:** Specifies the source URL of the image.
  - **alt:** Provides alternative text for the image (useful for accessibility).
  - **srcset:** Specifies multiple image sources with different resolutions.
  - **sizes:** Defines the preferred display size of the image.

### Tips and Tricks in HTML

- **Use HTML Entities**

  Use HTML entities for special characters (e.g., `&lt`; for <, `&gt`; for >, `&amp;` for &). This prevents rendering issues and ensures proper encoding.

  ```html
  <p>&lt;h1&gt;Hello, World!&lt;/h1&gt;</p>
  ```

  <p>&lt;h1&gt;Hello, World!&lt;/h1&gt;</p>

- **Use Line Breaks**

  Use line breaks (e.g., `<br>` or `<br />`) to create paragraphs and sections in HTML. This improves readability and makes it easier to style and structure the content.

  ```html
  <p>Paragraph 1<br />Paragraph 2</p>
  ```

- **Comment Out Code**

  Use comments (`<!-- Comment goes here -->`) to explain complex or important parts of your HTML code. Comments are not displayed on the webpage and can be helpful for other developers.

- **Validate HTML Code**
  Ensure your HTML code is valid by validating it with an HTML validator like the W3C Markup Validation Service. Valid HTML reduces the risk of rendering issues in different browsers.

- **Use Semantic HTML**

  Use semantic HTML elements to organize and structure your HTML code. Semantic HTML makes it easier for search engines to understand and index your content.

  ```html
  <header>
    <h1>My Website</h1>
    <nav>
      <ul>
        <li><a href="#">Home</a></li>
        <li><a href="#">About</a></li>
        <li><a href="#">Contact</a></li>
      </ul>
    </nav>
  </header>
  <main>
    <section>
      <h2>Section Title</h2>
      <p>Section content...</p>
    </section>
  </main>
  <footer>
    <p>&copy; 2023 My Website. All rights reserved.</p>
  </footer>
  ```

- **Lazy Loading Images**

  Use the `loading="lazy"` attribute to load images lazily. This helps to improve page load time and reduce bandwidth usage.

  ```html
  <img src="image.jpg" alt="Description of the image" loading="lazy" />
  ```

- **Use WebP Images**

  Use WebP images when possible. WebP images are lossless and can be used in all modern browsers.

  ```html
  <img src="image.webp" alt="Description of the image" />
  ```

- **Use SVGs**

  Use SVGs when possible. SVG images are scalable and can be used in all modern browsers.

  ```html
  <img src="image.svg" alt="Description of the image" />
  ```

- **Use Font Awesome**

  Use Font Awesome icons when possible. Font Awesome provides a consistent, consistent, and consistent set of icons that can be used in any project.

  ```html
  <i class="fa-solid fa-bell"></i>
  ```

- **contenteditable**

  Use the `contenteditable` attribute to make content editable. This allows you to add and edit content in your HTML code.

  ```html
  <p contenteditable="true">Hello, World!</p>
  ```

- **`<pre>`**

  Use the `pre` element to display code in a readable format. This can help to improve the readability of your code.

  ```html
  <pre>
    <code>
      function hello() {
        console.log("Hello, World!");
      }
    </code>
  </pre>
  ```

- **SELF-CLOSING Tags**

  Use the `self-closing` tags (`<br>`, `<img>`, and `<input>`) . which dont require a closing tag.

  ```html
  <br />
  <img src="image.jpg" alt="Description of the image" />
  <input type="text" />
  ```

- **`<noscript>`**

  Use the `noscript` element to display content only when JavaScript is not supported. This can help to improve the user experience.

  ```html
  <noscript>
    <p>JavaScript is not supported.</p>
  </noscript>
  ```

### Conclusion 📖

These notes provide a solid foundation for understanding HTML and how it is used in web development. HTML is a critical skill for anyone looking to create web content, and these topics cover the essential elements and techniques required. As you continue your web development journey, you can build upon this knowledge to create rich and interactive web experiences.

Happy Coding!!
