+++
title = 'Factory Functions and Classes in JavaScript'
date = 2024-02-22T13:15:45+05:30
draft = false
+++

In JavaScript, both factory functions and classes provide ways to create and manage objects, but they do so using different approaches and philosophies.

## Factory Functions:

A factory function is simply a function that returns a new object. Factory functions are often used for creating multiple instances of similar objects. One of the key features of factory functions is that they can take advantage of closures to create private variables and methods. This means that you can encapsulate certain details within the function scope, making them inaccessible from the outside world.

Example of a Factory Function:

```js
function createBook(title, author) {
  return {
    title,
    author,
    getDescription() {
      return `${title} by ${author}`;
    },
  };
}

const book1 = createBook("1984", "George Orwell");
console.log(book1.getDescription()); // Output: "1984 by George Orwell"
```

In this example, createBook is a factory function that returns a new object each time it is called. The object contains properties title and author, as well as a method getDescription. This method accesses the object's properties via closure, a mechanism that can be used to create private variables.

## Classes:

Introduced in ECMAScript 2015 (ES6), classes in JavaScript are syntactic sugar over the existing prototype-based inheritance and offer a more traditional object-oriented way to deal with objects and inheritance. A class defines a type of object according to a blueprint, which is instantiated using the new keyword. Classes support constructors, instance methods, static methods, and inheritance.

Example of a Class:

```js
class Book {
  constructor(title, author) {
    this.title = title;
    this.author = author;
  }

  getDescription() {
    return `${this.title} by ${this.author}`;
  }
}

const book1 = new Book("1984", "George Orwell");
console.log(book1.getDescription()); // Output: "1984 by George Orwell"
```

Here, the Book class serves as a blueprint for book objects. The new Book(...) syntax creates instances of Book, each with its own title and author properties and access to the getDescription method defined on Book's prototype.

**Main Differences:**

**Syntax and Structure:** Factory functions use plain functions and object literals, while classes use the class, constructor, and new keywords, offering a structure that might be more familiar to developers with a background in classical object-oriented languages.

**Inheritance:** While factory functions can achieve inheritance through object composition, classes provide a more straightforward and intuitive syntax for inheritance using extends and super.

**Encapsulation:** Factory functions can easily create private variables and functions using closures, a feature that requires more workarounds in classes (although private class fields, introduced in ES2020, offer this capability with a different syntax).

Let see more details on inheritance and encapsulation in the next section.

## Inheritance:

**Classes:**
Classes in JavaScript offer a clear and concise syntax for inheritance through the extends keyword. This allows one class to inherit properties and methods from another. The super keyword is used within the constructor of the subclass to call the constructor of the superclass, ensuring the superclass is correctly initialized.

Example of Class Inheritance:

```js
class Book {
  constructor(title, author) {
    this.title = title;
    this.author = author;
  }

  getDescription() {
    return `${this.title} by ${this.author}`;
  }
}

class EBook extends Book {
  constructor(title, author, format) {
    super(title, author);
    this.format = format;
  }
}

const book1 = new EBook("1984", "George Orwell", "PDF");
console.log(book1.getDescription()); // Output: "1984 by George Orwell"
console.log(book1.format); // Output: "PDF"
```

**Factory Functions:**
Factory functions can implement inheritance through object composition. This involves creating an object that serves as the prototype for another object, effectively allowing one object to inherit behavior from another.

Example of Inheritance with Factory Functions:

```js
function createBook(title, author) {
  return {
    title,
    author,
    getDescription() {
      return `${title} by ${author}`;
    },
  };
}

function createEBook(title, author, format) {
  const book = createBook(title, author);
  return Object.create(book, {
    format: {
      value: format,
      enumerable: true,
    },
  });
}

const book1 = createEBook("1984", "George Orwell", "PDF");
console.log(book1.getDescription()); // Output: "1984 by George Orwell"
console.log(book1.format); // Output: "PDF"
```

## Encapsulation

Factory Functions:

Factory functions naturally support encapsulation through closures. This means that any variables or functions defined within the factory function are only accessible within the function itself, not from the outside.

Example of Encapsulation with Factory Functions:

```js
function createCounter() {
  let count = 0; // `count` is private
  return {
    increment() {
      count++;
      console.log(count);
    },
    decrement() {
      count--;
      console.log(count);
    },
  };
}

const counter = createCounter();
counter.increment(); // Output: 1
counter.decrement(); // Output: 0
// There's no way to access `count` directly from outside `createCounter`.
```


**Classes:**

With the introduction of private class fields in ES2020, classes now offer a more straightforward syntax for encapsulation. Private fields are defined by prefixing the property name with #, making them accessible only within the class itself.

Example of Encapsulation with Classes:

```js
class Counter {
    #count = 0; // `#count` is a private field

    increment() {
        this.#count++;
        console.log(this.#count);
    }

    decrement() {
        this.#count--;
        console.log(this.#count);
    }
}

const counter = new Counter();
counter.increment(); // Output: 1
counter.decrement(); // Output: 0
// There's no way to access `#count` directly from outside `Counter`.

```

In summary, while both factory functions and classes in JavaScript can achieve inheritance and encapsulation, they do so in distinct ways. Factory functions offer a flexible approach using closures and object composition, whereas classes provide syntactic sugar for inheritance and encapsulation, making the code easier to read and maintain, especially for those familiar with object-oriented programming. 


