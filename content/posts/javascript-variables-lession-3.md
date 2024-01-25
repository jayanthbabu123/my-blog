+++
title = 'Javascript Variables Lession 3'
date = 2024-01-08T22:30:22+05:30
draft = false
categories = ['Javascript Learning']
image= "/images/js-variables.webp"
tags=[
    "Javascript",
    "Variables",
    "Javascript Variables",
    "Web Development",
    "Frontend Development",
    "Javascript Basics",
    "Javascript Syntax",
    "Javascript Types",
]
+++

![Javascript Variables Lession 3](/images/js-variables.webp)
## Introduction

Variables are like containers that store data values in JavaScript. You can declare a variable by specifying its name and optionally setting an initial value. JavaScript offers `var`, `let`, and `const` for variable declarations, each with its unique features and use cases.

In this blog, we'll explore the `var` keyword, which is essential for variable declaration in JavaScript.

## Utilizing var for Variable Declaration

Historically, `var` has been the primary method for declaring variables in JavaScript. It's used as follows:

```javascript
var name = "John";
```

## Rules for Variable Naming with var

- Begin with a letter, underscore (\_), or dollar sign ($).
- Include letters, numbers, underscores, or dollar signs.
- Variables are case-sensitive (e.g., `userName` and `UserName` are different).
- Avoid reserved keywords (e.g., `var`, `function`, `if`).

**Valid Variables:**

```javascript
var name = "Alice"; // Starts with a letter
var _age = 30; // Starts with an underscore
var $salary = 50000; // Starts with a dollar sign
var firstName = "John"; // CamelCase for multi-word names
var user_name = "Alice"; // Underscored for multi-word names
var FirstName = "Jane"; // PascalCase for multi-word names
```

**Invalid Variables:**

```javascript
var 2ndName = 'Smith';    // Invalid: starts with a number
var user-name = 'Bob';    // Invalid: hyphen is not allowed
var var = 123;            // Invalid: 'var' is a reserved keyword
var function = 'user';    // Invalid: 'function' is a reserved keyword
var @name = 'Alice';      // Invalid: '@' is not allowed
```

## Declaring Multiple Variables

JavaScript allows declaring multiple variables in a single statement, separated by commas. This approach can make your code more concise but should be used judiciously to maintain readability.

```javascript
var x = 10,
  y = 20,
  z = 30;
```

### Updating Variables with var

Updating a variable involves reassigning a new value to an already declared variable. This process does not require repeating the var keyword.

```javascript
var message = "Welcome to JavaScript!";
message = "Happy Coding!"; // Updating the value
```

To update a variable in JavaScript, just assign a new value to the variable instead of re-declaring it.

### Dynamic Typing in JavaScript

JavaScript's dynamic typing means the type of a variable can change based on the assigned value.

```javascript
var x = 10; // x is a number
x = "Hello"; // x is now a string
```

## Re-declaring Variables with var

JavaScript allows the re-declaration of a variable using var without any errors. However, this can be confusing and lead to bugs in your code.

```javascript
var x = 10;
var x = 20;
```

## Conclusion

The `var` keyword is essential for variable declaration in JavaScript. Adhering to the rules for variable naming and understanding the scope of `var` is crucial for effective JavaScript programming. Mastery of these concepts associated with `var` ensures a solid foundation in handling variables within the language.
