# Section A: Theory Questions

## Programming Fundamentals

### 1. What is programming and why is it important?

Programming is the process of designing and writing instructions that computers can execute to perform tasks. It is important because it enables the creation of software, automation of processes, and solving real-world problems.

### 2. Three key stages of programming

1. **Think** – Analyze the problem and plan a solution.
2. **Write** – Convert the solution into code using a programming language.
3. **Run & Iterate** – Execute the code, test it, fix errors, and improve the solution.

### 3. Why should code be written for humans first?

Code should be written for humans first because developers spend more time reading and maintaining code than writing it. Clear code improves collaboration and reduces errors.

### 4. Examples of problems programming can solve

* Online banking
* E-commerce systems
* Healthcare management
* Traffic control systems
* Education platforms
* Business automation

---

## JavaScript Fundamentals

### 1. What is JavaScript?

JavaScript is a high-level programming language primarily used to create interactive web pages. It was created by Brendan Eich in 1995.

### 2. Evolution of JavaScript

* **1995:** Created as Mocha, later renamed LiveScript and then JavaScript.
* **1997:** Standardized as ECMAScript.
* **2009:** Node.js enabled server-side JavaScript.
* **2015:** ES6 introduced major improvements.
* **Today:** Used for web, mobile, desktop, cloud, and server applications.

### 3. Where JavaScript can run

* Web browsers (Chrome, Firefox, Safari, Edge)
* Node.js servers
* Mobile applications (React Native)
* Desktop applications (Electron)

### 4. What is ECMAScript?

ECMAScript is the official standard specification that defines how JavaScript should work.

### 5. Impact of Node.js

Node.js allowed JavaScript to run outside the browser, enabling server-side development and full-stack JavaScript applications.

---

## Variables and Data Types

### 1. Difference between var, let, and const

* **var** is function-scoped and can be redeclared.
* **let** is block-scoped and can be reassigned.
* **const** is block-scoped and cannot be reassigned after initialization.

### 2. Why is const preferred?

const is preferred because it prevents accidental reassignment and makes code more predictable.

### 3. Primitive Data Types

* **String:** Text data (e.g., "Hello")
* **Number:** Numeric values (e.g., 42, 3.14)
* **Boolean:** true or false
* **Null:** Intentional absence of a value
* **Undefined:** Declared but not assigned a value

### 4. Purpose of typeof

The `typeof` operator returns the data type of a value.

### 5. Template Literals

Template literals use backticks (`) and allow embedded expressions with `${}`. They make string formatting easier and more readable.

---

## Functions and Control Flow

### 1. What is a function?

A function is a reusable block of code designed to perform a specific task.

### 2. Traditional Functions vs Arrow Functions

* Traditional functions use the `function` keyword.
* Arrow functions use `=>` syntax.
* Arrow functions do not have their own `this` binding.

### 3. Default Parameters

Default parameters provide predefined values when arguments are not supplied.

### 4. Conditional Statements

Conditional statements (`if`, `else if`, `else`) allow programs to make decisions based on conditions.

### 5. Loops

A loop repeatedly executes code while a condition is true. It is useful for processing collections of data or performing repetitive tasks.

---

## Modern JavaScript

### 1. Destructuring

Destructuring is a syntax that extracts values from arrays or properties from objects into variables.

### 2. Spread Operator and Rest Parameter

The spread operator (`...`) expands elements, while the rest parameter (`...`) collects multiple values into an array.

### 3. Optional Chaining

Optional chaining (`?.`) prevents errors when accessing properties of `null` or `undefined` values.

### 4. Async/Await

`async/await` makes asynchronous code easier to read, write, and maintain compared to callbacks.

### 5. map() and filter()

* `map()` transforms each element and returns a new array.
* `filter()` returns elements that satisfy a condition.

### 6. Benefits of ES6+

ES6+ features improve readability, maintainability, performance, and developer productivity.

---

# Section B: JavaScript Practical Questions

## 1. Variables and Template Literal

```javascript
const name = "Jacob";
const age = 25;
const favoriteLanguage = "JavaScript";

console.log(`My name is ${name}, I am ${age} years old, and my favorite programming language is ${favoriteLanguage}.`);
```

## 2. Positive, Negative, or Zero Check

```javascript
const number = 10;

if (number > 0) {
  console.log("Positive");
} else if (number < 0) {
  console.log("Negative");
} else {
  console.log("Zero");
}
```

## 3. greetUser Function

```javascript
function greetUser(name) {
  return `Hello, ${name}! Welcome.`;
}
```

## 4. Arrow Function to Multiply Two Numbers

```javascript
const multiply = (a, b) => a * b;

console.log(multiply(4, 5));
```

## 5. Loop from 1 to 20

```javascript
for (let i = 1; i <= 20; i++) {
  console.log(i);
}
```



Here is the link to my completed assignment:

[Download Assignment PDF]([Training purpose.]
