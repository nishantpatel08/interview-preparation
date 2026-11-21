# JavaScript Interview Questions

## Table of Contents

- [1. Core JavaScript Concepts](#1-core-javascript-concepts)
  - [1.1 Variables](#11-variables)
  - [1.2 Data Types](#12-data-types)
  - [1.3 Scope](#13-scope)
  - [1.4 Hoisting](#14-hoisting)
  - [1.5 Type Coercion](#15-type-coercion)
  - [1.6 Equality](#16-equality)
  - [1.7 Operators](#17-operators)
- [2. Functions and Scope](#2-functions-and-scope)
  - [2.1 Arrow Functions](#21-arrow-functions)
  - [2.2 Callbacks](#22-callbacks)
  - [2.3 Lexical Scope](#23-lexical-scope)
  - [2.4 Closures](#24-closures)
  - [2.5 Higher-Order Functions](#25-higher-order-functions)
  - [2.6 this Keyword](#26-this-keyword)
- [3. Objects and Data Handling](#3-objects-and-data-handling)
  - [3.1 Destructuring](#31-destructuring)
  - [3.2 Spread and Rest Operators](#32-spread-and-rest-operators)
  - [3.3 Prototypes](#33-prototypes)
  - [3.4 Classes](#34-classes)
  - [3.5 Array Methods](#35-array-methods)
  - [3.6 Immutability](#36-immutability)
- [4. Asynchronous JavaScript](#4-asynchronous-javascript)
  - [4.1 Event Loop](#41-event-loop)
  - [4.2 Promises](#42-promises)
  - [4.3 Async/Await](#43-asyncawait)
  - [4.4 Microtasks](#44-microtasks)
  - [4.5 Timers](#45-timers)
  - [4.6 Error Handling](#46-error-handling)
- [5. JavaScript Runtime and Architecture](#5-javascript-runtime-and-architecture)
  - [5.1 Execution Context](#51-execution-context)
  - [5.2 Call Stack](#52-call-stack)
  - [5.3 Memory Management](#53-memory-management)
  - [5.4 Garbage Collection](#54-garbage-collection)
  - [5.5 Event Delegation](#55-event-delegation)
  - [5.6 Modules](#56-modules)

## 1. Core JavaScript Concepts

### 1.1 Variables

**Q. What are variables in JavaScript?**

Variables are used to store data. JavaScript provides three ways to declare variables: var, let, and const.
- var: Function-scoped and can be redeclared and reassigned.
- let: Block-scoped and can be reassigned but not redeclared in the same scope.
- const: Block-scoped and cannot be reassigned after initialization.

### 1.2 Data Types

**Q. What are the data types in JavaScript?**

JavaScript has two categories of data types:
- Primitive: String, Number, Boolean, Undefined, Null, BigInt, and Symbol.
- Non-primitive: Objects, including arrays and functions.
Primitive values hold individual values, while objects can represent collections of properties and values.

### 1.3 Scope

**Q. What is scope in JavaScript?**

Scope determines where a variable can be accessed in the code.

There are three main types:
- Global scope: Accessible throughout the program.
- Function scope: Accessible within the function where it is declared.
- Block scope: Accessible within a block {} when declared using let or const.

### 1.4 Hoisting

**Q. What is hoisting in JavaScript?**

Hoisting is JavaScript's behavior of processing declarations before executing the code in their scope.
- var declarations are hoisted and initialized with undefined.
- let and const are hoisted but cannot be accessed before initialization because they are in the Temporal Dead Zone (TDZ).
- Function declarations can generally be called before their definition.

### 1.5 Type Coercion

**Q. What is type coercion in JavaScript?**

Type coercion is the process of converting a value from one data type to another.

There are two types:
- Implicit coercion: JavaScript converts the type automatically.
- Explicit coercion: The developer converts the type manually using methods such as Number(), String(), or Boolean().

### 1.6 Equality

**Q. What is the difference between == and ===?**

- == compares values after performing type coercion when necessary.
- === compares both value and type without type coercion.
In general, === is preferred because it avoids unexpected type conversions.

### 1.7 Operators

**Q. What are operators in JavaScript?**

Operators are symbols used to perform operations on values and variables.

Common types include:
- Arithmetic: +, -, *, /, %, **
- Comparison: >, <, >=, <=, ==, ===
- Logical: &&, ||, !
- Assignment: =, +=, -=
- Unary: typeof, ++, --
- Nullish coalescing: ??
- Optional chaining: ?.
These operators are used to calculate values, compare data, assign values, and control how expressions are evaluated.

## 2. Functions and Scope

### 2.1 Arrow Functions

**Q. What are arrow functions in JavaScript?**

Arrow functions provide a shorter syntax for writing functions. They do not have their own this; instead, they inherit it from the surrounding scope.
```javascript
const add = (a, b) => a + b;
```

### 2.2 Callbacks

**Q. What is a callback function in JavaScript?**

A callback is a function passed as an argument to another function and executed by that function.
```javascript
function greet(callback) {
  callback();
}
```

```javascript
greet(() => console.log("Hello"));
```

Callbacks are commonly used in event handling, asynchronous operations, and array methods.

### 2.3 Lexical Scope

**Q. What is lexical scope in JavaScript?**

Lexical scope means a function can access variables defined in its own scope and in its outer scope, based on where the function is written.
```javascript
const name = "John";
```

```javascript
function greet() {
  console.log(name);
}
```

Here, greet() can access name because it is defined in the outer scope.

### 2.4 Closures

**Q. What is a closure in JavaScript?**

A closure occurs when a function remembers and can access variables from its outer lexical scope, even after the outer function has finished executing.
```javascript
function outer() {
  let count = 0;

  return function () {
    count++;
    return count;
  };
}
```

```javascript
const counter = outer();
console.log(counter()); // 1
console.log(counter()); // 2
```

Closures are commonly used for data privacy, maintaining state, and creating function factories.

### 2.5 Higher-Order Functions

**Q. What is a higher-order function in JavaScript?**

A higher-order function is a function that accepts another function as an argument, returns a function, or does both.
```javascript
function calculate(a, b, operation) {
  return operation(a, b);
}
```

```javascript
console.log(calculate(5, 3, (a, b) => a + b)); // 8
```

Common examples include map(), filter(), and reduce().

### 2.6 this Keyword

**Q. What is this in JavaScript?**

The this keyword refers to a value determined by how a function is called. In a regular function, its value depends on the calling context. Arrow functions inherit this from their surrounding lexical scope.
```javascript
const user = {
  name: "John",
  greet() {
    console.log(this.name);
  }
};
```

```javascript
user.greet(); // John
```

Here, this refers to the user object because the method is called using user.greet().

## 3. Objects and Data Handling

### 3.1 Destructuring

**Q. What is destructuring in JavaScript?**

Destructuring is a feature that allows us to extract values from arrays or properties from objects and assign them to variables easily.
```javascript
const user = { name: "John", age: 25 };
const { name, age } = user;
```

```javascript
const numbers = [10, 20];
const [a, b] = numbers;
```

### 3.2 Spread and Rest Operators

**Q. What is the spread operator in JavaScript?**

The spread operator (...) expands elements of an array or properties of an object.
```javascript
const a = [1, 2];
const b = [...a, 3, 4];
```

**Q. What is the rest operator in JavaScript?**

The rest operator (...) collects multiple values into a single array or object.
```javascript
function sum(...numbers) {
  return numbers.reduce((total, n) => total + n, 0);
}
```

Key difference: Spread expands values, while rest collects values. The syntax is the same, but the usage differs.

### 3.3 Prototypes

**Q. What are prototypes in JavaScript?**

A prototype is an object from which another object can inherit properties and methods. JavaScript uses the prototype chain to look up properties that are not found directly on an object.

This mechanism is called prototypal inheritance.

### 3.4 Classes

**Q. What are classes in JavaScript?**

Classes provide a cleaner syntax for creating objects and implementing inheritance. They use JavaScript's prototype-based inheritance internally.
```javascript
class User {
  constructor(name) {
    this.name = name;
  }

  greet() {
    return `Hello ${this.name}`;
  }
}
```

Classes can also use extends to inherit from another class and super() to call the parent constructor.

### 3.5 Array Methods

**Q. What are some commonly used array methods in JavaScript?**

- map(): Creates a new array by transforming each element.
- filter(): Creates a new array containing elements that match a condition.
- reduce(): Reduces an array to a single accumulated result.
- find(): Returns the first element that matches a condition.
- forEach(): Executes a callback for each element.
- some(): Checks whether at least one element matches a condition.
- every(): Checks whether all elements match a condition.
- sort(): Sorts the array in place by default.

**Q. What is the difference between map() and forEach()?**

map() returns a new array containing the callback's results, while forEach() executes a callback for each element and returns undefined.

### 3.6 Immutability

**Q. What is immutability in JavaScript?**

Immutability means not modifying existing data directly. Instead, we create a new value or object containing the required changes.
```javascript
const numbers = [1, 2, 3];
const updated = [...numbers, 4];
```

Here, numbers remains unchanged, and updated is a new array.

**Q. How can we update objects and arrays immutably?**

We can use the spread operator, methods such as map() and filter(), and other techniques that create new values instead of modifying the original data.

Important: Spread creates only a shallow copy. Nested objects may still be shared between the original and copied structures.

## 4. Asynchronous JavaScript

### 4.1 Event Loop

**Q. What is the event loop in JavaScript?**

The event loop allows JavaScript to handle asynchronous operations without blocking the main thread. It checks whether the call stack is empty and moves ready callbacks from queues to the call stack for execution.

### 4.2 Promises

**Q. What is a Promise in JavaScript?**

A Promise represents the eventual success or failure of an asynchronous operation.

A Promise has three states:
- Pending: Initial state.
- Fulfilled: Operation completed successfully.
- Rejected: Operation failed.
We commonly handle promises using .then(), .catch(), and .finally().

### 4.3 Async/Await

**Q. What are async and await in JavaScript?**

async and await provide a cleaner way to work with promises.
- async makes a function return a Promise.
- await pauses execution of the surrounding async function until the Promise settles, without blocking the main thread.
They make asynchronous code easier to read and maintain.

### 4.4 Microtasks

**Q. What are microtasks in JavaScript?**

Microtasks are high-priority queued tasks that run after the current synchronous code finishes and before the event loop proceeds to the next task.

Promise callbacks, such as .then() and .catch(), are common examples of microtasks.

### 4.5 Timers

**Q. How do setTimeout() and setInterval() work in JavaScript?**

- setTimeout() schedules a callback to run after a specified minimum delay.
- setInterval() schedules a callback to run repeatedly at a specified interval.
The callbacks do not execute immediately when the delay expires. They must wait until the call stack is available and the event loop can process them.

### 4.6 Error Handling

**Q. How do you handle errors in asynchronous JavaScript?**

Error handling depends on the asynchronous pattern:
- Promises: Use .catch().
- Async/await: Use try...catch.
- Synchronous code: Use try...catch where appropriate.
For async/await, try...catch is especially useful for handling rejected promises and preventing unhandled errors.

## 5. JavaScript Runtime and Architecture

### 5.1 Execution Context

**Q. What is an execution context in JavaScript?**

An execution context is the environment in which JavaScript code is evaluated and executed. It contains information about variables, functions, scope, and the value of this.

The main types are:
- Global execution context: Created when the JavaScript program starts.
- Function execution context: Created whenever a function is called.
- Eval execution context: Created when code is executed using eval().

### 5.2 Call Stack

**Q. What is the call stack in JavaScript?**

The call stack is a LIFO (Last In, First Out) data structure that tracks function calls during execution.

When a function is called, it is pushed onto the stack. When it finishes, it is popped off the stack.

If the stack grows too large, such as through infinite recursion, JavaScript can throw a stack overflow error.

### 5.3 Memory Management

**Q. How does memory management work in JavaScript?**

JavaScript automatically allocates memory when values and objects are created and reclaims memory when it is no longer needed.

The JavaScript engine manages this process, so developers generally do not need to allocate or free memory manually.

### 5.4 Garbage Collection

**Q. What is garbage collection in JavaScript?**

Garbage collection is the process of automatically identifying and reclaiming memory that is no longer reachable or needed by the program.

JavaScript engines commonly use a technique called mark-and-sweep, which identifies reachable objects and collects unreachable ones.

**Q. What is a memory leak in JavaScript?**

A memory leak occurs when memory that is no longer needed remains reachable, preventing the garbage collector from reclaiming it.

Common causes include unnecessary global variables, uncleared timers, and event listeners that are no longer needed.

### 5.5 Event Delegation

**Q. What is event delegation in JavaScript?**

Event delegation is a technique in which we attach a single event listener to a parent element instead of attaching separate listeners to multiple child elements.

It works through event bubbling and is useful for improving efficiency and handling dynamically added elements.

### 5.6 Modules

**Q. What are modules in JavaScript?**

Modules allow us to split code into separate files, making it easier to organize, maintain, and reuse.

JavaScript modules use:
- export to make functions, variables, or classes available to other modules.
- import to use exported values from another module.
There are two common module systems:
- ES Modules (ESM): Uses import and export.
- CommonJS (CJS): Uses require() and module.exports, commonly found in Node.js projects.