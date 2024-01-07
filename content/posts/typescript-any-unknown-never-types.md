+++
title = "TypeScript's any vs unknown vs never: Complete Guide"
date = 2023-12-21T12:46:53+05:30
draft = false
tags=[
    "TypeScript Tutorial",
    "JavaScript Superset",
    "TypeScript Types",
    "TypeScript any type",
    "TypeScript unknown type",
    "TypeScript never type",
    "Type Safety",
    "TypeScript Basics",
    "TypeScript Advanced Concepts",
    "TypeScript for Beginners",
    "Programming Best Practices",
    "Static Type Checking",
    "TypeScript Development",
    "TypeScript Guide",
    "TypeScript Type System",
    "Web Development",
    "Coding in TypeScript",
    "TypeScript Examples",
    "TypeScript Blog",
    "Learn TypeScript"
]
categories= ["TypeScript"]
image= "/images/typescript.webp"
+++
![Typescript types](/images/typescript.webp)

### Introduction 📘

TypeScript, a superset of JavaScript, enhances the language by adding static types. These types ensure better code quality and readability. In TypeScript, understanding the distinction between `any`, `unknown`, and `never` types is crucial for developers, especially beginners.

In this blog, we'll focus on breaking down these three types in a clear, straightforward manner. You'll learn what each type represents, when to use them, and the practical implications of incorporating them into your TypeScript projects. By the end of this post, you'll have a solid grasp of `any`, `unknown`, and `never`, empowering you to make informed decisions about type usage in your TypeScript development. Let's dive in and explore these key types!

### Declaring Basic Types in TypeScript 🏗️

Before diving into the specifics of `any`, `unknown`, and `never`, it's helpful to understand how TypeScript handles basic type declarations. This foundational knowledge will make it easier to grasp the more complex types.
TypeScript allows you to explicitly define the type of a variable. Here's a quick look at how you can declare variables with basic types:

```typescript
// Number
let age: number = 30;

// String
let name: string = "Alice";

// Boolean
let isActive: boolean = true;

// Array
let numbers: number[] = [1, 2, 3];

// Tuple
let person: [string, number] = ["Alice", 30];
```

Each of these declarations associates a variable with a specific type, ensuring that the correct type of value is always assigned to it. With this understanding, we can now explore the more complex types `any`, `unknown`, and `never`.

### 1. any: The Flexible Type 🤹

The any type in TypeScript allows you to use a variable as if it could be any data type. You can assign a `string`, `number`, `boolean`, `object`, or any other type to a variable declared with `any`. This type is useful when strict type enforcement is unnecessary or impractical, offering maximum flexibility.

**When and How to Use any?**

Use `any` when the type of a variable is unknown or can change, like with values from user input or external sources (APIs, libraries). However, remember that using `any` too much can lead to losing the benefits of TypeScript's type checking. It's usually a temporary solution or used in situations where precise type information is not available.

**Example:**

```typescript
let mystery: any = "a surprise!";

// Reassigning to different types
mystery = 42; // No error, now a number
mystery = false; // Still no error, now a boolean

// Performing operations typical of different types
console.log(mystery.toString()); // Works as a boolean

// Reassigning to an object
mystery = { key: "value" };
console.log(mystery.key); // No error, accessing property of an object
```

In this example, mystery is first a string, then changes to a number, a boolean, and finally an object. The lack of type errors demonstrates the flexibility of any. It can take on various forms and still allow operations typical of its current type.

### 2. unknown: The Safe and Versatile Type 🕵️‍♂️

The `unknown` type in TypeScript is used for variables whose type is not yet known and needs to be determined. It's a type-safe counterpart to any. While any allows you to do anything with the variable, `unknown` is more restrictive: you must first confirm its type through type checking before performing most operations on it.

**When and How to Use unknown?:**

`unknown` is ideal when you want to ensure type safety, especially when dealing with values from external sources like APIs or user input where the type isn't known upfront. It's a way to tell TypeScript that the type needs to be checked before use. It helps in avoiding common mistakes that can occur when dealing with `unknown` types.

```typescript
let uncertainValue: unknown = "Hello World";

// Trying to use it directly will result in an error
// console.log(uncertainValue.toUpperCase()); // Error

// Type checking
if (typeof uncertainValue === "string") {
  console.log(uncertainValue.toUpperCase()); // Safe and works!
}
```

In this example, uncertainValue is initially of type unknown. TypeScript prevents operations like toUpperCase until the type is confirmed through a type check `(typeof uncertainValue === 'string')`. This ensures safety in operations.

**Additional Simple Example for unknown**

In this example, we'll handle an unknown type that could be either a string or an array of numbers:

```typescript
let unknownValue: unknown = ["one", 2, "three", 4];

// Directly using unknownValue as an array will cause an error
// console.log(unknownValue.length); // Error

// Type checking for an array
if (Array.isArray(unknownValue)) {
  // Safe to use as an array
  unknownValue.forEach((item) => {
    if (typeof item === "string") {
      console.log(`String: ${item}`);
    } else if (typeof item === "number") {
      console.log(`Number: ${item}`);
    }
  });
}
```

In this example, `unknownValue` could be an array, but TypeScript requires us to verify its type first. We use `Array.isArray()` to check if it's an array and then iterate over its elements. For each element, we further check if it's a string or a number before performing any operations. This showcases how unknown can be used to ensure type safety in complex structures.

### 3. never: The Type for Unreachable States ⛔

The never type represents values that never occur. It's used in scenarios where a value will never be returned, like in functions that always throw an error or in infinite loops. It's a way for TypeScript to understand and enforce that certain code paths will not be reached or values not produced.

**When and How to Use never?:**
Use `never` when writing a function that is not expected to return a value ever or in exhaustive type checks where every possible case has been covered and returning a value becomes impossible.
**Example:**

```typescript
function throwError(message: string): never {
  throw new Error(message);
}

throwError("Something went wrong"); // This function doesn't return anything
```

In this example, the throwError function is marked with the `never` type because it always throws an error and never reaches a return point. This is a straightforward use case for `never`, indicating functions that do not complete normally.

**Additional Simple Example for never**

Imagine we have a union type representing different kinds of pets and a function that handles each kind. We'll use `never` to ensure that every possible pet type is handled:

```typescript
// Union type for different kinds of pets
type Pet = "dog" | "cat" | "fish";

// Function to handle different pet types
function handlePet(pet: Pet) {
  switch (pet) {
    case "dog":
      console.log("Handle a dog");
      break;
    case "cat":
      console.log("Handle a cat");
      break;
    case "fish":
      console.log("Handle a fish");
      break;
    default:
      // Ensures that every possible type of Pet is handled
      const exhaustiveCheck: never = pet;
      return exhaustiveCheck;
  }
}

handlePet("dog"); // Outputs: "Handle a dog"
// handlePet('bird'); // TypeScript error: Type '"bird"' is not assignable to type 'Pet'.
```

In this example, `handlePet` is a function that accepts a Pet type, which can be either 'dog', 'cat', or 'fish'. The `never` type in the default case ensures that all cases of Pet are handled. If you try to pass a value like 'bird' that is not part of the Pet type, TypeScript will produce a compile-time error, preventing the code from compiling. This is because 'bird' is not assignable to the Pet type, demonstrating TypeScript's ability to catch such errors early in the development process.

### When to Use Each Type 🚦

Use `any` when you're gradually moving from JavaScript to TypeScript or in complex dynamic logic where type safety is not a priority.

Use `unknown` for better type safety when dealing with dynamic content or third-party libraries, where the type of data is uncertain.

Use `never` in situations where you want to ensure a function doesn't return anything or for exhaustive type checking.

### Conclusion 🌟

Understanding `any`, `unknown`, and `never` is crucial for effective TypeScript development. While `any` provides flexibility, `unknown` offers safety, and `never` ensures certain conditions are unattainable. Use them wisely to harness the full power of TypeScript's type system.

Incorporating these types into your TypeScript projects will help you write more robust and maintainable code. Remember, the key is to balance flexibility with safety.

Happy coding!
