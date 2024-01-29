+++
title = 'Javascript Strings and Methods - Lession 9'
date = 2024-01-27T23:53:06+05:30
draft = false
categories = ['Javascript Learning']
image= "/images/js-strings.webp"
tags=[
    "Javascript",
    "Javascript Strings",
    "Web Development",
    "Frontend Development",
    "Javascript Basics",
    "Javascript Syntax",
    "Javascript Types",
    "Javascript Methods",
    "String Methods"
]
weight = 9
+++

![Javascript Strings and Methods - Lession 9](/images/js-strings.webp)

## Introduction 🌱

In JavaScript, strings represent textual data. They can be declared in three ways, as shown in the following code snippet:

```javascript
// Using single quotes
let str1 = "Hello";

// Using double quotes
let str2 = "World";

// Using backticks (template literals)
let str3 = `Hello World`;
```

Each method of declaring strings has its own benefits, with backticks allowing for string interpolation and multi-line strings.

## 1. String Length 📏

To get the length of a string, we use the .length property. This returns the number of characters in the string.

```javascript
let str = "Hello";
console.log(str.length); // Outputs: 5
```

## 2. Extracting String Characters in JavaScript 🔍

String characters in JavaScript can be extracted using several methods. Each method has its unique characteristics and use cases.

### 2.1. Using Property Access [] 🗝️

JavaScript strings can be accessed like arrays. If you use an index to access a character and the index is out of range, it returns undefined.

```javascript
let str = "JavaScript";
console.log(str[0]); // Outputs: 'J'
console.log(str[100]); // Outputs: undefined
```

This method provides a more concise and familiar syntax for those accustomed to array-like access. However, it's less safe than `charAt()` as it can return undefined.

### 2.2. The at(position) Method 🔢

Introduced in ECMAScript 2021, the `at()` method retrieves the character at a given index. It accepts positive and negative integers, where negative integers count back from the last character, offering an easier approach to access characters from the end. It is a modern addition to the language, addressing some limitations of the older `charAt()` method.

```javascript
let str = "JavaScript";
console.log(str.at(0)); // Outputs: 'J'
console.log(str.at(-1)); // Outputs: 't' (last character)
```

Ideal for accessing characters from the end without calculating the length.

### 2.3. The charAt() Method 🔤

The `charAt()` method returns the character at a specific position in a string. If the index you supply is out of range, it returns an empty string.

```javascript
let str = "JavaScript";
console.log(str.charAt(0)); // Outputs: 'J'
console.log(str.charAt(100)); // Outputs: ''
```

It's widely supported and was the standard way to access individual characters before at() was introduced.

### 2.4. The charCodeAt() Method 🔠

This method returns the Unicode integer representing the character at the specified position. It's helpful for understanding the underlying numeric representation of a character.

```javascript
let str = "JavaScript";
console.log(str.charCodeAt(0)); // Outputs: 74
console.log(str.charCodeAt(100)); // Outputs: NaN
```

This method is useful for getting a character's numerical representation. It helps in scenarios where character encoding matters, like sorting or converting characters.

## 3. Extracting String Parts in JavaScript 🔪

Extracting specific parts of a string is a common operation in JavaScript. This can be achieved using several methods, each tailored for different scenarios.

### 3.1. Using slice(startIndex, endIndex) 🍰

The slice() method extracts a section of a string and returns it as a new string without modifying the original string. It can take positive and negative indices. A negative index indicates an offset from the end of the string.

```javascript
let str = "Hello, World!";
console.log(str.slice(7, 12)); // Outputs: 'World'
console.log(str.slice(-6, -1)); // Outputs: 'World'
console.log(str.slice(-1)); // Outputs: '!'
console.log(str.slice(7)); // Outputs: 'World!'
```

Ideal for extracting substrings when you know the start and end indices. Its ability to handle negative indices makes it versatile for various scenarios.

### 3.2. Using substring(startIndex, endIndex) ✂️

Similar to `slice()`, but `substring()` differs in how it handles negative indices and the order of indices. `Negative` or `NaN` values are treated as 0. If endIndex is less than startIndex, substring() swaps the two arguments.

```javascript
let str = "Hello, World!";
console.log(str.substring(7, 12)); // Outputs: 'World'
console.log(str.substring(12, 7)); // Also outputs: 'World'
```

Best used when working with positive indices. Its behavior of swapping indices can be advantageous in certain situations.

### 3.3. Using substr(startIndex, length) 📌

This method extracts a substring from a string, starting at a specified index and extending for a given number of characters. Note that substr() is considered a legacy feature and may be removed in future versions of JavaScript.

```javascript
let str = "Hello, World!";
console.log(str.substr(7, 5)); // Outputs: 'World'
```

Useful for extracting a substring when you know the `start index` and the `length` of the substring. However, due to its deprecation status, it's better to use `slice()` or `substring()` in modern JavaScript development.

## 4. indexOf() and includes() Methods 🔎

## 4.1 The indexOf() Method 🔍

The indexOf() method returns the index of the first occurrence of a specified value in a string. If the value is not found, it returns -1. This method is case-sensitive.

```javascript
let str = "Hello, World!";
console.log(str.indexOf("World")); // Outputs: 7
console.log(str.indexOf("world")); // Outputs: -1 (case-sensitive)
console.log(str.indexOf("o", 5)); // Outputs: 8 (search starts from index 5)
```

Ideal for finding the position of a substring in a string. It's especially useful in situations where you need to check if a substring exists and know its position for further processing.

### 4.2 The includes() Method ✔️

The includes() method checks if a string contains a specified substring. It returns a Boolean value: true if the string contains the specified value, otherwise false. This method is also case-sensitive.

```javascript
let str = "Hello, World!";
console.log(str.includes("World")); // Outputs: true
console.log(str.includes("world")); // Outputs: false (case-sensitive)
console.log(str.includes("Hello", 1)); // Outputs: false (search starts from index 1)
```

`includes()` is perfect for checking the presence of a substring without needing its exact position. This method is commonly used in conditionals to determine if a specific part of a string is present.

### 5. Upper and Lower Case Methods 🔠🔡

In JavaScript, strings can be easily converted to upper case or lower case. This functionality is essential for formatting, comparing, or processing text data.

```javascript
let str = "Hello, World!";
console.log(str.toUpperCase()); // Outputs: "HELLO, WORLD!"
console.log(str.toLowerCase()); // Outputs: "hello, world!"
```

In this example, `toUpperCase()` converts the entire string to uppercase, while `toLowerCase()` converts the entire string to lowercase.

## 6. More String Methods 🛠️

Lets explore some more string methods in JavaScript

## 6.1. Concat Method 🔗

The `concat()` method in JavaScript is used to join two or more strings together. It concatenates the string arguments it receives and returns a new string without altering the original strings.

```javascript
let greet = "Hello, ";
let name = "Alice";
let message = "have a great day!";

let fullMessage = greet.concat(name, ", ", message);
console.log(fullMessage); // Outputs: "Hello, Alice, have a great day!"
```

While `concat()` is a valid method, `string interpolation` with `template literals` (using backticks \`\`) is often preferred in modern JavaScript for readability and ease of use.

## 6.2. Split Method 🧩

The `split()` method in JavaScript is used to split a string into an array of substrings. It takes a separator as an argument and returns an array of substrings.

```javascript
let str = "Hello, World!";
console.log(str.split()); // Outputs: ["Hello, World!"]
console.log(str.split(",")); // Outputs: ["Hello", " World!"]
console.log(str.split("")); // Outputs: ["H", "e", "l", "l", "o", ",", " ", "W", "o", "r", "l", "d", "!"]
```

## 6.3. Trim Method ✂️

The `trim()` method in JavaScript is used to remove whitespace from both ends of a string. It returns a new string without modifying the original string.

```javascript
let str = "   Hello, World!   ";
console.log(str.trim()); // Outputs: "Hello, World!"
```

## 6.4. Repeat Method 🔁

The `repeat()` method in JavaScript is used to repeat a string a specified number of times. It takes a number as an argument and returns a new string with the repeated string.

```javascript
let str = "Hello, World!";
console.log(str.repeat(3)); // Outputs: "Hello, World!Hello, World!Hello, World!"
```

## Conclusion

In summary, JavaScript's string methods are essential tools for developers, providing powerful and efficient ways to manipulate text data. From basic operations like changing case to advanced techniques like extracting and searching for substrings, these methods enhance the functionality and interactivity of web applications. Mastering these string methods is a fundamental step in your journey as a JavaScript developer, enabling you to handle text data with ease and precision.
