+++
title = 'Javascript Numbers and Its Methods - Lession 10'
date = 2024-01-27T23:54:36+05:30
draft = false
categories = ['Javascript Learning']
image= "/images/js-numbers.webp"
tags=[
    "Javascript",
    "Javascript Numbers",
    "Web Development",
    "Frontend Development",
    "Javascript Basics",
    "Javascript Syntax",
    "Javascript Types",
    "Javascript Methods",
    "Number Methods"
]
weight = 10
+++

![Javascript Numbers and Its Methods - Lession 10](/images/js-numbers.webp)

## Introduction 🌱

JavaScript offers a versatile set of number data types and methods to handle various numerical operations. Numbers in JavaScript can be represented in different forms such as `integers`, `floating-point numbers`, `exponential notation`, and `BigInts`. Let's explore these types with examples:

```javascript
let age = 10; // Integer
let price = 99.99; // Floating-point number
let largeNumber = 1e6; // Equals 1 million // Exponential notation
let bigNumber = 9007199254740991n; // BigInt
```

Let's explore some `Numbers` Methods in JavaScript with examples:

## 1. toString()

The `toString()` method is used to convert a number to a string. It returns a string representation of the number.

```javascript
let num = 123;
let str = num.toString();
console.log(str); // Outputs: '123'
```

## 2. Number.isFinite()

This static method determines whether the passed value is a finite number. Unlike the global `isFinite()` function, this method does not forcibly convert the argument to a number. This means it returns true only if the argument is of the type Number and is finite.

```javascript
console.log(Number.isFinite(25)); // Outputs: true
console.log(Number.isFinite("25")); // Outputs: false
console.log(Number.isFinite(Infinity)); // Outputs: false
```

## 3. Number.isInteger()

`Number.isInteger()` checks whether a value is an integer. This method is useful for validation processes where determining if a value is a whole number is crucial.

```javascript
console.log(Number.isInteger(10)); // Outputs: true
console.log(Number.isInteger(10.5)); // Outputs: false
console.log(Number.isInteger("10")); // Outputs: false
```

## 4. toFixed()

The `toFixed()` method is used to convert a number to a string with a specified number of decimal places. It returns a string representation of the number.

```javascript
let num = 2.34567;
console.log(num.toFixed(2)); // Outputs: '2.35'
console.log(num.toFixed(0)); // Outputs: '2'
```

## 5. parseInt()

The `parseInt()` method is used to convert a string to an integer. It returns an integer representation of the string.

```javascript
let str = "123";
console.log(parseInt(str)); // Outputs: 123
console.log(parseInt("123.45")); // Outputs: 123
```

## 6. parseFloat()

The `parseFloat()` method is used to convert a string to a floating-point number. It returns a floating-point number representation of the string.

```javascript
console.log(parseFloat("123.45")); // Outputs: 123.45
console.log(parseFloat("123.00")); // Outputs: 123
console.log(parseFloat("123.45abc")); // Outputs: 123.45
```

## 7. toLocaleString()

This method converts a number to a string, using locale-specific formatting. This is extremely useful for displaying numbers in a format familiar to the user, such as `currency formatting`, `comma separators`, etc.

```javascript
let num = 1222123;
console.log(num.toLocaleString()); // Outputs: '1,222,123'
console.log(num.toLocaleString("en-US")); // Outputs: '1,222,123'
console.log(num.toLocaleString("de-DE")); // Outputs: '1.222.123'
console.log(num.toLocaleString("fr-FR")); // Outputs: '1 222 123'
```

In JavaScript, Number methods like Number.isFinite() and Number.isInteger() are specific functions of the Number object, designed for precise operations on numeric values. They are used directly on the Number object itself and cater to more specialized number-related tasks. On the other hand, global functions such as parseInt() and parseFloat() are not tied to any object and can be used independently for broader purposes. These global functions are typically utilized for converting strings to numbers and handling general numeric operations.

## Conclusion 📝

Each of these methods serves a specific purpose in handling and manipulating numbers in JavaScript. Whether you're formatting numbers for display, parsing numeric strings, or validating numerical data types, these methods provide the necessary functionality for a broad range of applications
