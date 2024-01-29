+++
title = 'JavaScript Objects and All its Methods'
date = 2024-01-27T23:55:03+05:30
draft = false
categories = ['Javascript Learning']
image= "/images/js-object-methods.webp"
tags=[
    "Javascript",
    "Javascript Objects",
    "Web Development",
    "Frontend Development",
    "Javascript Basics",
    "Javascript Syntax",
    "Javascript Types",
    "Javascript Methods",
    "Object Methods"
]
weight = 11
+++

![Javascript Objects and Its Methods - Lession 11](/images/js-object-methods.webp)

In JavaScript objects are collections of properties, where each property is a key-value pair. Objects in JavaScript are versatile and fundamental to most JavaScript applications, allowing you to store, manipulate, and transmit data in a structured way.

## 1. Declaring Objects in JavaScript

Creating objects in JavaScript is a fundamental skill, as objects are key components in the language. There are several methods to declare objects, each with its own use cases:

## 1.1 Object Literals

This is the most straightforward and commonly used method for creating objects. It's ideal for simple objects with a known set of properties at the time of creation.

```javascript
let person = {
  name: "John",
  age: 30,
};
```

## 1.2 The new Object() Syntax

The `new` keyword is used to create objects using the `Object()` constructor. It is a common method for creating objects in JavaScript. This approach is less common and is generally used when creating an object from a built-in JavaScript constructor like `Object()`.

```javascript
let person = new Object();
person.name = "John";
person.age = 30;
```

It can be useful in more dynamic situations, but typically, object literals are preferred for their simplicity.

## 1.3 Constructor Functions

Constructor functions are ideal when you need to create multiple similar objects. They provide a blueprint for creating objects of the same type.

```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
}
let person = new Person("Alice", 30);
```

It promotes code reusability and encapsulation. Useful in object-oriented programming patterns.

## 1.4 Object.create()

The `Object.create()` method is used to create an object using an existing object as a prototype. It is useful when you need to create a new object from an existing object.

```javascript
const prototypeObj = { role: "Developer" };
let person = Object.create(prototypeObj);
```

This provides a clear way to set up inheritance in objects. It allows for the creation of an object without having to define a constructor function.

Each of these methods has its own use cases and advantages. The choice of which method to use depends on the specific requirements of your application and your personal or team's coding style preferences. Object literals are sufficient for simple, standalone objects, while constructor functions, Object.create(), and class syntax are more suited for creating multiple objects with similar properties and methods.

## 2. Manipulating Object Properties

To access or change the properties of an object, you can use the dot notation, or the bracket notation. Both methods are used interchangeably.

## 2.1 Adding Properties

We can add the properties to an object in two ways: using dot notation or bracket notation.

```javascript
let user = {
  name: "John",
};

user.age = 30;
user["country"] = "India";

console.log(user); // Outputs: { name: "John", age: 31, city: "New York" }
```

`age`: Using dot notation (user.age = 30;), we add the age property and set its value to 30.
`country`: Using bracket notation (`user["country"] = "India";`), we add the country property with the value "India". This method is especially useful for property names that are dynamic or not valid identifiers.

## 2.2 Modifying Properties

To modify the properties of an object, we can use the dot notation or bracket notation.

```javascript
let user = {
  name: "John",
  age: 30,
  country: "India",
};

user.age = 31;
user["country"] = "USA";
```

`age`: Using dot notation (user.age = 31;), we modify the age property to 31.
`country`: Using bracket notation (`user["country"] = "USA";`), we modify the country property to "USA".

## 2.3 Deleting Properties

The delete operator removes a specified property from an object. To delete a property from an object, we can use the dot notation or bracket notation. This is the same approach like above.

```javascript
let user = {
  name: "John",
  age: 30,
  country: "India",
};

delete user.age;
delete user["country"];
```

3. Looping Through Object Properties

To loop through the properties of an object, we can use the for...in loop. This is similar to the way we loop through arrays, but it iterates over properties of an object.

```javascript
let user = {
  name: "John",
  age: 30,
};

for (let key in user) {
  console.log(key); // Outputs: name, age
  console.log(user[key]); // Outputs: John, 30
}
```

## 4. All JavaScript Object Methods

JavaScript provides a variety of methods for interacting with objects. These methods offer powerful ways to manipulate, examine, and transform object data. Let's explore some of these key methods with informative descriptions and examples.

## 4.1 Object.keys()

The `Object.keys()` method is used to get an array of the keys of an object. It returns an array of the keys of the object.

```javascript
let user = {
  name: "John",
  age: 30,
};

let keys = Object.keys(user);
console.log(keys); // Outputs: ["name", "age"]
```

## 4.2 Object.values()

Similar to Object.keys(), this method returns an array of the values of the own enumerable string properties of an object.

```javascript
let user = {
  name: "John",
  age: 30,
};

let values = Object.values(user);
console.log(values); // Outputs: ["John", 30]
```

## 4.3 Object.entries()

The `Object.entries()` method is used to get an array of the key-value pairs of an object. It returns an array of the key-value pairs of the object.

```javascript
let user = {
  name: "John",
  age: 30,
};

let entries = Object.entries(user);
console.log(entries); // Outputs: [["name", "John"], ["age", 30]]
```

## 4.4 JSON.parse() & JSON.stringify()

`JSON.stringify()` Converts a JavaScript object into a JSON string. `JSON.parse() `Parses a JSON string into a JavaScript object.

```javascript
let user = {
  name: "John",
  age: 30,
};

let json = JSON.stringify(user);
console.log(json); // Outputs: '{"name":"John","age":30}'

let obj = JSON.parse(json);
console.log(obj); // Outputs: { name: "John", age: 30 }
```

## 4.5 Object.assign()

The `Object.assign()` method is used to copy the properties of one or more source objects to a target object. It returns the target object.

```javascript
let user = {
  name: "John",
  age: 30,
};

let clone = Object.assign({}, user);
console.log(clone); // Outputs: { name: "John", age: 30 }
```

## 4.6 Object.freeze()

`Object.freeze()` Freezes an object. A frozen object can no longer be changed; freezing an object prevents new properties from being added, existing properties from being removed, and prevents changing the enumerability, configurability, or writability of existing properties.

```javascript
let user = {
  name: "John",
  age: 30,
};

Object.freeze(user);
user.name = "Pete";
delete user.age;
user.isAdmin = true;
console.log(Object.isFrozen(user)); // Outputs: true
console.log(user); // Outputs: { name: "John", age: 30 }
```

## 4.7 Object.seal()

`Object.seal()` Prevents new properties from being added to an object and marks all existing properties as non-configurable. Properties can still be modified.

```javascript
let user = {
  name: "John",
  age: 30,
};

Object.seal(user);
user.name = "Pete";
delete user.age;
user.isAdmin = true;
console.log(Object.isSealed(user)); // Outputs: true
console.log(user); // Outputs: { name: "Pete", age: 30 }
```

## 4.8 Object.is()

`Object.is()` Compares if two values are the same value. It's similar to the strict equality (===) operator, but it also treats NaN as equal to NaN (which === does not).

```javascript
console.log(Object.is(0, -0)); // Outputs: false
console.log(Object.is(0, 0)); // Outputs: true
console.log(Object.is(NaN, NaN)); // Outputs: true
console.log(Object.is({ name: "John" }, { name: "John" })); // Outputs: false
```

Each of these methods serves a specific purpose in object manipulation and inspection, making them invaluable tools in a JavaScript developer's toolkit. Understanding and utilizing these methods can significantly enhance your ability to work effectively with JavaScript objects.

## Conclusion 📝

understanding JavaScript objects and their methods is fundamental for practical web development. These concepts are essential for effectively managing and manipulating data in real-world applications. Mastery of these skills enables developers to build more dynamic, efficient, and robust web solutions, making them indispensable in the toolkit of any web developer.
