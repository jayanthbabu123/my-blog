+++
title = 'Es6 Classes in Javascript Lession 23'
date = 2024-02-17T13:05:59+05:30
draft = false
+++

# Introduction

ES6 (ECMAScript 2015) introduced a significant enhancement to JavaScript with the introduction of classes. Classes in JavaScript provide a more structured and familiar syntax for defining object blueprints, closely resembling the class-based inheritance model found in other programming languages like Java and C++.

In JavaScript, classes act as blueprints for creating objects with shared properties and methods. They offer a familiar syntax for developers coming from languages with class-based inheritance models.

Through classes, developers can define constructors to initialize object instances, create properties to hold data, and declare methods to perform actions related to the class.

Classes also support features like private properties and methods, static properties and methods, and inheritance, enabling developers to build complex applications with ease.

Understanding how to use classes in JavaScript is essential for creating scalable and maintainable codebases. In this guide, we'll explore the core concepts of ES6 classes, including constructors, properties, methods, and advanced features, to empower you in your JavaScript development journey.

# 1. How to Write Classes, Naming Conventions, Hoisting

In JavaScript, writing classes follows a straightforward syntax introduced in ES6. The class keyword serves as the foundation for defining classes, providing a clear structure for object-oriented programming.

```javascript
class MyClass {
  // Class body
}
```

## Naming Conventions

Following naming conventions enhances code readability and maintainability. In JavaScript, class names typically start with a capital letter to distinguish them from regular functions or variables.

```javascript
class Car {
  // Class body
}
```

Using descriptive and meaningful names for classes helps developers understand their purpose and functionality at a glance.

## Hoisting

Unlike function declarations, class declarations are not hoisted in JavaScript. This means that you cannot access a class before its declaration in the code.

```javascript
const car = new Car(); // ReferenceError: Cannot access 'Car' before initialization

class Car {
  // Class body
}
```

It's important to declare classes before using them to avoid runtime errors. This ensures that classes are properly defined and accessible throughout the codebase.

## 2. Constructor

In JavaScript classes, the constructor method serves as a special function used for initializing newly created objects. It is called automatically when an instance of the class is created, allowing developers to set up initial state and perform necessary setup tasks.

```javascript
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  // Class body
}
```

**Key Features of Constructors:**

**Initialization:** The primary purpose of the constructor is to initialize object properties based on the arguments passed during object creation.

**Parameterized:** Constructors can accept parameters, enabling dynamic initialization of object properties based on external values.

**Execution:** The constructor is automatically executed whenever a new instance of the class is created using the new keyword.

**Single Constructor:** A class can only contain one constructor method. If multiple constructors are defined, JavaScript will throw a SyntaxError.

**Default Constructor:** If a constructor is not explicitly defined within a class, JavaScript provides a default constructor that initializes the object with no additional behavior.

example:

```javascript
class Car {
  constructor(make, model, year) {
    this.make = make;
    this.model = model;
    this.year = year;
  }
}

const myCar = new Car("Toyota", "Corolla", 2022);
```

In this example, the Car class has a constructor that initializes the make, model, and year properties of each Car instance created.

Constructors are essential for ensuring that objects are properly initialized and ready for use. They provide a convenient way to set initial state and perform setup tasks, contributing to the overall structure and functionality of JavaScript classes. Understanding constructors is foundational for effective object-oriented programming in JavaScript.

## 3. Properties in JavaScript Classes

In JavaScript classes, properties are variables that hold data associated with class instances. These properties define the state of objects created from the class and are accessed using dot notation (.) or bracket notation ([]).

```javascript
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
}
```

Key Features of Properties:

Declaration and Initialization: Properties are typically declared and initialized within the constructor method using the this keyword followed by the property name. However, properties can also be declared outside the constructor, allowing for more flexibility in class definitions.

Access Modifiers: By default, properties in JavaScript classes are public and can be accessed and modified from outside the class. However, ES6 does not support private or protected properties natively.

Dynamic Nature: Properties in JavaScript classes are dynamic, meaning they can be added, modified, or removed during runtime.

```javascript
class Person {
  city = "Hyderabad";
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
}

const person = new Person("John", 30);
console.log(person.city); // Output: 'Hyderabad'
console.log(person.name); // Output: 'John'
console.log(person.age); // Output: 30
```

In this example, the Person class defines three properties: city, name, and age. The city property is initialized with a default value of 'Hyderabad' and is accessible from outside the class. The name and age properties are initialized using the constructor method. The name and age properties are also accessible from outside the class.

## 4. Methods

In JavaScript classes, methods are functions defined within the class that perform specific actions related to the class or its instances. Methods encapsulate behavior, allowing for modular and reusable code.

```javascript
class Rectangle {
  constructor(width, height) {
    this.width = width;
    this.height = height;
  }

  calculateArea() {
    return this.width * this.height;
  }
}
```

**Key Features of Methods:**

Declaration: Methods are defined within the class body using standard function syntax. They can access class properties using the this keyword.

Purpose: Methods encapsulate behavior associated with class instances. They perform actions, manipulate data, or compute values based on the state of the object.

Access Modifiers: Like properties, methods are public by default in JavaScript classes. They can be accessed and invoked from outside the class.

Prototype Inheritance: Methods defined within a class are shared among all instances of that class. They are stored in the prototype object and are not duplicated for each instance.

```javascript
class Circle {
  constructor(radius) {
    this.radius = radius;
  }

  calculateArea() {
    return Math.PI * this.radius ** 2;
  }

  calculateCircumference() {
    return 2 * Math.PI * this.radius;
  }
}

const myCircle = new Circle(5);
console.log(myCircle.calculateArea()); // Output: 78.54
console.log(myCircle.calculateCircumference()); // Output: 31.42
```

In this example, the Circle class defines methods `calculateArea()` and `calculateCircumference()` to compute the area and circumference of a circle based on its radius.

Understanding methods is essential for defining the behavior of JavaScript classes. Methods enable classes to exhibit functionality, perform operations, and interact with data, making them a fundamental aspect of object-oriented programming in JavaScript.

## 5. Creating Objects with Classes in JavaScript

In JavaScript, objects are instances of classes, created using the new keyword followed by the class name and optional arguments passed to the class constructor. This process is fundamental for creating instances with unique properties and behaviors defined by the class blueprint.

```javascript
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
}

const person1 = new Person("John", 30);
const person2 = new Person("Alice", 25);
```

## Key Points for Creating Objects with Classes:

Instantiation: Objects are instantiated from classes using the new keyword, followed by the class name and constructor arguments (if any).

Constructor Invocation: When an object is created, the class constructor is automatically invoked to initialize the object properties based on the provided arguments.

Unique Instances: Each object created from a class is a unique instance with its own set of properties and values, independent of other instances created from the same class.

Object Methods: Objects inherit methods defined within the class, allowing them to perform actions and interact with data based on the class functionality.

```javascript
class Car {
  constructor(make, model, year) {
    this.make = make;
    this.model = model;
    this.year = year;
  }

  displayDetails() {
    console.log(`${this.year} ${this.make} ${this.model}`);
  }
}

const car1 = new Car("Toyota", "Corolla", 2022);
const car2 = new Car("Honda", "Accord", 2021);

car1.displayDetails(); // Output: 2022 Toyota Corolla
car2.displayDetails(); // Output: 2021 Honda Accord
```

In this example, the Car class defines properties and a method to display car details. Two instances of Car objects (car1 and car2) are created with different property values.

Understanding how to create objects with classes is essential for object-oriented programming in JavaScript. It allows developers to define reusable templates (classes) and instantiate objects with specific properties and behaviors, promoting code reusability and maintainability.

## 6. Private Properties in JavaScript Classes

In JavaScript, the concept of private properties refers to class properties that are not directly accessible or modifiable from outside the class. While JavaScript does not have native support for private properties, the introduction of the hash (#) symbol in ES2022 provides a way to simulate private properties by using name mangling.

```javascript
class Person {
  #name;
  #age;

  constructor(name, age) {
    this.#name = name;
    this.#age = age;
  }

  displayDetails() {
    console.log(`Name: ${this.#name}, Age: ${this.#age}`);
  }
}

const person1 = new Person("John", 30);
person1.displayDetails(); // Output: Name: John, Age: 30
person1.#age; // Output: ReferenceError: Cannot access private property '#age'
```

In this example, the Person class defines a private property `#name` and `#age`. The name and age properties are private and can only be accessed and modified within the class.

**Key Features of Private Properties**:

Declaration with # Symbol: Private properties are declared using the hash (#) symbol followed by the property name within the class body.

Encapsulation: Private properties are encapsulated within the class, preventing direct access or modification from external code. They are only accessible within the class methods.

Name Mangling: The use of the hash symbol is a form of name mangling, making it challenging for external code to unintentionally interfere with private properties.

## 7. Private Methods in JavaScript Classes

In JavaScript, private methods are class methods that cannot be accessed or invoked from outside the class. While JavaScript does not have native support for private methods, developers can achieve privacy by using closures or naming conventions. However, with the introduction of the hash (#) symbol in ES2022, private methods become feasible.

```javascript
class BankAccount {
  #balance = 0;

  #validateAmount(amount) {
    return typeof amount === "number" && amount > 0;
  }

  #updateBalance(amount) {
    this.#balance += amount;
  }

  constructor(initialBalance) {
    this.#balance = initialBalance;
  }

  deposit(amount) {
    if (this.#validateAmount(amount)) {
      this.#updateBalance(amount);
      console.log(`Deposited $${amount}. New balance: $${this.#balance}`);
    } else {
      console.error("Invalid deposit amount.");
    }
  }

  withdraw(amount) {
    if (this.#validateAmount(amount) && amount <= this.#balance) {
      this.#updateBalance(-amount); // Negative amount for withdrawal
      console.log(`Withdrawn $${amount}. New balance: $${this.#balance}`);
    } else {
      console.error("Invalid withdrawal amount or insufficient funds.");
    }
  }

  #logTransaction(action, amount) {
    console.log(
      `Transaction: ${action}. Amount: $${amount}. Balance: $${this.#balance}`
    );
  }
}

const account = new BankAccount(1000);
account.deposit(500);
account.withdraw(200);
```

Declaration with # Symbol: Private methods are declared using the hash (#) symbol followed by the method name within the class body.

Encapsulation: Private methods are encapsulated within the class, preventing direct access or invocation from external code. They are only accessible within other class methods.

Access Control: Private methods can be used to encapsulate internal functionality or validation logic, enhancing code organization and readability.

Name Mangling: The use of the hash symbol makes private methods less prone to accidental invocation or interference from external code.

In the provided example, the BankAccount class demonstrates the use of private methods #validateAmount, #updateBalance, and #logTransaction. These methods encapsulate validation, balance update, and transaction logging functionalities, respectively, ensuring that they are only accessible and used within the class itself.

Private methods improve code encapsulation and security by restricting access to sensitive class functionality. While JavaScript does not natively support private methods, the introduction of the hash symbol enables developers to implement privacy features, enhancing the robustness and maintainability of JavaScript classes.

## 8.Static Properties and Methods in JavaScript Classes

In JavaScript classes, static properties and methods belong to the class itself rather than instances of the class. They are accessed directly from the class, not from instances, and are often used for utility functions or properties that are shared among all instances of the class.

**Static Properties:**

Static properties are declared using the static keyword within the class body.

```javascript
class Circle {
  static PI = 3.14;
  static defaultRadius = 5;
}
```

Static properties are declared using the static keyword within the class body. They are accessed directly from the class itself, not from instances of the class.

```javascript
console.log(Circle.PI); // Output: 3.14
console.log(Circle.defaultRadius); // Output: 5
```

**Static Methods:**

Static methods are also declared using the static keyword within the class body. They are called directly on the class itself, not on instances of the class.

```javascript
class MathUtils {
  static square(x) {
    return x * x;
  }

  static cube(x) {
    return x * x * x;
  }
}

console.log(MathUtils.square(3)); // Output: 9
console.log(MathUtils.cube(2)); // Output: 8
```

In the provided example, the MathUtils class defines two static methods: square and cube. They are called directly on the MathUtils class, not on instances of the class.

Static properties and methods are not available on instances of the class created with the new keyword.

```javascript
const circleInstance = new Circle();
console.log(circleInstance.PI); // Output: undefined
console.log(circleInstance.defaultRadius); // Output: undefined
```

Understanding static properties and methods is essential for defining shared functionality and data within JavaScript classes. They provide a way to encapsulate utility functions and shared constants, promoting code organization and reusability. However, it's important to note that static properties and methods are not tied to instances of the class and must be accessed directly from the class itself.

## 9. Inheritance in JavaScript Classes

Inheritance is a fundamental concept in object-oriented programming that enables one class (subclass) to inherit properties and methods from another class (superclass). JavaScript supports inheritance through the extends keyword, allowing for the creation of a hierarchical relationship between classes.

```javascript
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log("Animal speaks");
  }
}

class Dog extends Animal {
  bark() {
    console.log("Dog barks");
  }
}

const dog = new Dog("Max");
dog.speak(); // Output: 'Animal speaks'
dog.bark(); // Output: 'Dog barks'
```

In the provided example, the Animal class defines a constructor and a speak method. The Dog class inherits from the Animal class by using the extends keyword. The Dog class defines a bark method.

**Key Points:**

_Subclassing:_ The subclass (derived class) inherits properties and methods from the superclass (base class).

**Extends Keyword:** The extends keyword is used to create a subclass of a superclass.

**Super Keyword:** The super keyword is used to call methods of the superclass within the subclass constructor.

```javascript
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(`${this.name} speaks`);
  }
}

class Dog extends Animal {
  constructor(name, breed) {
    super(name); // Call the superclass constructor
    this.breed = breed;
  }

  bark() {
    console.log(`${this.name} barks`);
  }
}

const myDog = new Dog("Buddy", "Golden Retriever");
myDog.speak(); // Output: Buddy speaks
myDog.bark(); // Output: Buddy barks
```
In this example, the Dog class inherits the `speak()` method from the `Animal` class and defines its own `bark()` method. The `super(name)` call in the Dog constructor invokes the constructor of the Animal superclass, ensuring that the name property is properly initialized.

**Considerations:**

**Single Inheritance:** JavaScript supports single inheritance, meaning a class can only inherit from one superclass.

**Method Overriding:** Subclasses can override methods inherited from the superclass, providing a customized implementation.

In conclusion, understanding inheritance is essential for creating scalable and modular JavaScript applications. It enables the development of class hierarchies and promotes code reuse, leading to more maintainable and efficient codebases.

## 10. Getter and Setter Methods in JavaScript Classes

In JavaScript, getters and setters are methods that are used to provide read and write access to class properties. Getters and setters are defined using the get and set keywords, respectively.

Getter and setter methods are special types of methods in JavaScript classes that allow controlled access to class properties. They are used to retrieve or modify the value of a class property, respectively.

```javascript
class Circle {
  constructor(radius) {
    this.radius = radius;
  }

  get diameter() {
    return this.radius * 2;
  }

  set diameter(diameter) {
    this.radius = diameter / 2;
  }
}

const circle = new Circle(5);
console.log(circle.diameter); // Output: 10
circle.diameter = 20;
console.log(circle.radius); // Output: 10
```

In this example, the diameter getter method calculates and returns the diameter of the circle based on the radius property. The diameter setter method modifies the radius property based on the diameter value.

Setter methods are used to set the value of a property in an object. They are defined using the set keyword followed by the method name.

```javascript
class Circle {
  constructor(radius) {
    this.radius = radius;
  }

  get diameter() {
    return this.radius * 2;
  }

  set diameter(value) {
    this.radius = value / 2;
  }
}

const myCircle = new Circle(5);
console.log(myCircle.diameter); // Output: 10

myCircle.diameter = 12;
console.log(myCircle.radius); // Output: 6

```
In this example, the diameter setter method sets the radius property of the circle based on the provided diameter value.

While it's true that in JavaScript, properties can be accessed and modified directly, using getter and setter methods provides several advantages:

**Encapsulation:** Getter and setter methods help encapsulate the internal representation of an object's state. They allow you to control how properties are accessed and modified, providing a level of abstraction that hides the internal implementation details. This enhances the modularity and maintainability of your codebase.

**Validation and Data Integrity:** Getter and setter methods enable you to enforce validation rules and ensure data integrity. For example, you can validate input values before setting a property, preventing invalid or unexpected data from being assigned to it.

**Computed Properties:** Getter methods allow you to compute and return values based on the current state of the object. This is particularly useful for derived or computed properties that depend on other properties within the object.

While direct property access is simple and convenient, using getter and setter methods provides a more controlled and robust approach to working with object properties. It promotes good software engineering practices such as encapsulation, abstraction, and data validation, leading to more maintainable and resilient codebases.

## 11. Composition over Inheritance in JavaScript Classes

Composition over inheritance is a design principle in object-oriented programming that suggests favoring object composition over class inheritance. Instead of relying solely on class inheritance hierarchies, composition allows you to construct more flexible and modular code by composing objects from smaller, more reusable components.

**Key Principles:**

**Encapsulation:** Composition promotes encapsulation by breaking down complex functionalities into smaller, self-contained components. Each component handles a specific aspect of behavior or functionality, making the codebase easier to understand and maintain.

**Flexibility and Reusability:** Composition allows you to reuse existing components across different parts of your application. This promotes code reusability and reduces redundancy, as you can assemble different combinations of components to create new functionalities without relying on deep class hierarchies.

**Reduced Coupling:** Inheritance creates tight coupling between classes in a hierarchy, making it challenging to change or extend functionality without affecting other parts of the system. Composition, on the other hand, promotes loose coupling by allowing objects to interact through well-defined interfaces, reducing dependencies and making the codebase more modular and adaptable.

```javascript
// Example of Composition
class Engine {
  start() {
    console.log('Engine started');
  }

  stop() {
    console.log('Engine stopped');
  }
}

class Car {
  constructor() {
    this.engine = new Engine();
  }

  start() {
    this.engine.start();
    console.log('Car started');
  }

  stop() {
    this.engine.stop();
    console.log('Car stopped');
  }
}

const myCar = new Car();
myCar.start();
myCar.stop();

```

In this example, the Car class uses composition to incorporate the functionality of the Engine class. Instead of inheriting from the Engine class, the Car class has an instance of the Engine class as one of its properties. This approach allows for greater flexibility, as the Car class can use any type of engine without being tightly coupled to a specific implementation.

Composition simplifies the codebase by promoting a modular design where each component has a single responsibility. This makes the code easier to understand, maintain, and extend over time.

## 12. Conclusion

JavaScript classes are a fundamental feature of modern JavaScript, introduced in ES6, and provide a more structured and object-oriented approach to programming. They enable developers to create reusable and modular code by encapsulating data and behavior into objects. Classes support inheritance, allowing for code reuse and the creation of class hierarchies. Additionally, they offer features like static methods, getter/setter methods, and method chaining, enhancing code readability and maintainability. Understanding classes in JavaScript is essential for building robust and scalable applications in the language.







