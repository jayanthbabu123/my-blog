+++
title = 'How to Generate QR Code in React'
date = 2023-12-25T09:58:24+05:30
draft = false
favorite = true
tags = [
    "React Tutorial",
    "QR Code Generation",
    "React QR Code",
    "Web Development",
    "ReactJS",
    "JavaScript Library",
    "qrcode.react",
    "Frontend Development",
    "React Components",
    "Coding QR Codes",
    "React Programming",
    "QR Code in React",
    "Interactive Web Apps",
    "React for Beginners",
    "Modern Web Development",
    "React Development",
]
weight = 8

categories = ["React"]
image = "/images/qr-code.webp"
+++
![How to generate QR Code in React](/images/qr-code.webp)

### Introduction 🌟
Welcome to web development, a place where smart ideas come to life! In this blog, we'll explore a really cool feature - generating QR Codes in a React application. QR Codes are everywhere, from restaurant menus to event tickets, offering a quick way to access websites, text, and other data. Whether you're building a personal project or enhancing your business app, integrating QR Codes can significantly uplift your user experience. 

Let's get started and see how QR Codes can make your app more interactive and fun!
### Prerequisites 🛠️
For this tutorial, we're assuming that you already have a React project set up and running locally. If you need help setting up a React project, there are plenty of resources available online to guide you through the process.

### What is a QR Code?🤔
A QR Code (Quick Response Code) is a two-dimensional barcode that stores information in a grid of tiny squares. It's commonly used to link directly to websites, text, emails, or phone numbers.

### Step 1: Install the QR Code Library 📥
Before adding a QR Code to your app, you need the right tool. We'll use qrcode.react, a simple yet powerful library for this task.

Open your project's terminal and Run the following command to install the library by navigating into your project directory:
```bash
npm install qrcode.react
```

This command fetches and installs the QR Code library, making it ready to use in your project.
### Step 2: Import the QRCode Component 📲
Once the library is installed, the next step is to import it into your React component. In your App.js file, add the import statement for the QRCode component at the top:
```jsx
import React from 'react';
import QRCode from 'qrcode.react';

function App() {
  // The rest of your component code will go here
}

export default App;
```

This line makes the QRCode component available for use within your App component.

### Step 3: Add the QRCode Component to Your App 🎨
With the QRCode component imported, you can now use it in your app's render output. Update your App function to include the QRCode component. Here, we'll encode a URL into the QR Code:

```jsx
import React from 'react';
import QRCode from 'qrcode.react';

function App() {
  return (
    <div className="App">
      <h2>Your QR Code:</h2>
      <QRCode value="https://programwithjayanth.com/" />
    </div>
  );
}

export default App;

```
In this example, the QRCode component is rendering a QR Code for the URL "https://programwithjayanth.com/". The `<h2>` tag above it provides a simple heading. This setup will display a QR Code on the screen when you run your React application.

### Step 4: Style Your QR Code ⚙️
A touch of CSS can make the QR Code blend more elegantly with your app's design. Add some CSS to your App.css file:
```css
.App {
  text-align: center;
  margin-top: 50px;
}
```

This CSS centers the QR Code in your app and adds some margin at the top for better spacing.
### Step 5: Customize Your QR Code 
Customizing your QR Code involves setting various properties on the QRCode component, like size, colors, and error correction level. These properties allow you to tailor the QR Code's appearance to fit your app's design. Here's an enhanced version of the App.js with these customizations:

```jsx
import React from 'react';
import QRCode from 'qrcode.react';

function App() {
  return (
    <div className="App">
      <h2>Customized QR Code:</h2>
      <QRCode 
        value="https://programwithjayanth.com/"
        size={200} // setting the size to 200 pixels
        bgColor="#f8f8f8" // light grey background
        fgColor="#333333" // dark grey foreground
        level="H" // high error correction level
      />
    </div>
  );
}

export default App;
```
In this updated code, the QR Code is larger (200 pixels), and its colors are customized to fit a grey-themed design. The error correction level is set to 'H', which is the highest, allowing the QR Code to remain scannable even if part of it gets obscured. This customization enhances the visual appeal and functionality of the QR Code in your app.

### Step 6: Live Demo 🌐
For your convenience, I have created a demo of the React QR Code component on CodeSandbox. This demo allows you to see the QR Code generation in action and explore the code in a live environment. Feel free to interact with it and get a hands-on understanding of how the component works within a React application. View the CodeSandbox Demo here.

<iframe src="https://codesandbox.io/p/sandbox/qr-code-in-react-k438yt?file=%2Fsrc%2FApp.js" style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;" title="QR code in React"></iframe>

Try to scan the the above QR code, it will show you the URL https://programwithjayanth.com/. Feel free to experiment with these settings to see what looks best in your app.

### Conclusion 
And that's it! You now have a functional QR Code in your React application. This guide is just the beginning. As you become more comfortable with React and QR codes, you can explore more advanced features and customization options.

🎉 Enjoy adding this interactive element to your project. Happy Coding!!
