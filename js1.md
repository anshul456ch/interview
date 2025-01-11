

```markdown
# JavaScript Interview Questions and Examples

---

### **Q1. What is JavaScript, and what are its key features?**
**Answer:**  
JavaScript is a scripting language primarily used for enhancing web pages with dynamic content and interactivity. It is lightweight and versatile, supporting various programming paradigms such as object-oriented and functional programming. Key features include dynamic typing, prototypal inheritance, and first-class functions.

**Example:**
```javascript
// Dynamic content example
document.getElementById("demo").innerHTML = "Hello, World!";

// Object-oriented programming example
const person = {
  name: "John",
  greet: function() {
    console.log(`Hello, ${this.name}`);
  }
};
person.greet(); // Output: Hello, John
```

---

### **Q2. What are the data types in JavaScript?**
**Answer:**  
JavaScript has several built-in data types, including numbers, strings, booleans, null, undefined, and symbols (added in ES6). Additionally, objects and functions are considered reference types in JavaScript.

**Example:**
```javascript
let num = 10; // number
let str = "Hello"; // string
let bool = true; // boolean
let nullVar = null; // null
let undefinedVar; // undefined
let sym = Symbol("id"); // symbol
let obj = { name: "John" }; // object
let func = function() {}; // function
```

---

### **Q3. What is the difference between == and === operators?**
**Answer:**  
The `==` operator performs type coercion, meaning it attempts to convert the operands to the same type before comparing them. On the other hand, the `===` operator, also known as the strict equality operator, compares both the value and the type of the operands.

**Example:**
```javascript
console.log(5 == "5"); // true (type coercion)
console.log(5 === "5"); // false (strict comparison)
```

---

### **Q4. What is hoisting in JavaScript?**
**Answer:**  
Hoisting is a JavaScript behavior where variable and function declarations are moved to the top of their containing scope during the compilation phase. This means that you can access variables or functions before they are declared.

**Example:**
```javascript
console.log(x); // undefined (hoisted but not initialized)
var x = 5;

hoistedFunc(); // Output: Hello
function hoistedFunc() {
  console.log("Hello");
}
```

---

### **Q5. Explain the difference between let, const, and var.**
**Answer:**  
- `var` has function scope and can be redeclared and reassigned.
- `let` has block scope and can be reassigned but not redeclared.
- `const` has block scope and cannot be reassigned or redeclared.

**Example:**
```javascript
var a = 10; // function-scoped
let b = 20; // block-scoped
const c = 30; // block-scoped and immutable

if (true) {
  var a = 50; // redeclared
  let b = 60; // new block-scoped variable
  // const c = 70; // Error: cannot redeclare
}
console.log(a); // 50
console.log(b); // 20
```

---

### **Q6. What are arrow functions, and how do they differ from regular functions?**
**Answer:**  
Arrow functions are a concise way to write anonymous functions in JavaScript. They have a shorter syntax compared to regular functions and do not bind their own `this`, `arguments`, `super`, or `new.target`.

**Example:**
```javascript
// Regular function
function add(a, b) {
  return a + b;
}

// Arrow function
const addArrow = (a, b) => a + b;

console.log(add(2, 3)); // 5
console.log(addArrow(2, 3)); // 5
```

---

### **Q7. Explain event bubbling and event capturing in JavaScript.**
**Answer:**  
Event bubbling and event capturing are two phases of event propagation in the HTML DOM. Event capturing occurs during the capturing phase, where the event travels from the outermost element to the target element. Event bubbling occurs during the bubbling phase, where the event travels from the target element to the outermost element.

**Example:**
```html
<div id="parent">
  <button id="child">Click Me</button>
</div>

<script>
  document.getElementById("parent").addEventListener("click", () => {
    console.log("Parent clicked (capturing)");
  }, true); // Capturing phase

  document.getElementById("child").addEventListener("click", () => {
    console.log("Child clicked (bubbling)");
  }); // Bubbling phase
</script>
```

---

### **Q8. How can you prevent the default behavior of an event in JavaScript?**
**Answer:**  
You can prevent the default behavior of an event in JavaScript using the `preventDefault()` method. This method can be called on the event object within an event handler to prevent the browser’s default action associated with the event from occurring.

**Example:**
```javascript
document.querySelector("a").addEventListener("click", (e) => {
  e.preventDefault(); // Prevents the link from navigating
  console.log("Link clicked but default behavior prevented");
});
```

---

### **Q9. What is a closure in JavaScript, and how is it used?**
**Answer:**  
A closure is a combination of a function and the lexical environment within which the function was declared. Closures allow functions to access variables from their surrounding scope even after the outer function has finished executing.

**Example:**
```javascript
function outer() {
  let count = 0;
  return function inner() {
    count++;
    console.log(count);
  };
}

const counter = outer();
counter(); // 1
counter(); // 2
```

---

### **Q10. How does prototypal inheritance work in JavaScript?**
**Answer:**  
Prototypal inheritance in JavaScript allows objects to inherit properties and methods from their prototype object. When a property or method is accessed on an object, JavaScript first checks if the object has its own property or method. If not, it looks up the prototype chain until it finds the property or method.

**Example:**
```javascript
const parent = {
  greet() {
    console.log("Hello from parent");
  }
};

const child = Object.create(parent);
child.greet(); // Output: Hello from parent
```

---

### **Q11. What is the difference between null and undefined in JavaScript?**
**Answer:**  
- `null` represents the intentional absence of any value. It is explicitly assigned to a variable to indicate that it does not point to any object or value.
- `undefined` indicates that a variable has been declared but has not been assigned a value. It is the default value assigned to variables that have not been initialized.

**Example:**
```javascript
let a; // undefined
let b = null; // null

console.log(a); // undefined
console.log(b); // null
```

---

### **Q12. What are the different ways to declare variables in JavaScript?**
**Answer:**  
There are three ways to declare variables in JavaScript: using `var`, `let`, and `const` keywords. The `var` keyword has function scope, while `let` and `const` have block scope. Variables declared with `var` can be redeclared and reassigned, whereas variables declared with `let` can be reassigned but not redeclared. Variables declared with `const` cannot be reassigned or redeclared, and they must be assigned a value when declared.

**Example:**
```javascript
var x = 10; // function-scoped
let y = 20; // block-scoped
const z = 30; // block-scoped and immutable
```

---

### **Q13. What is the use of the ‘this’ keyword in JavaScript?**
**Answer:**  
The `this` keyword refers to the current execution context. Its value is determined by how a function is called, rather than where it is defined. In a global context, `this` refers to the global object (`window` in browsers). In a function context, `this` refers to the object that the function is a method of. It allows access to object properties and methods within a function.

**Example:**
```javascript
const obj = {
  name: "John",
  greet() {
    console.log(`Hello, ${this.name}`);
  }
};
obj.greet(); // Output: Hello, John
```

---

### **Q14. Explain the concept of event delegation in JavaScript.**
**Answer:**  
Event delegation is a JavaScript technique where a single event listener is attached to a parent element, rather than multiple event listeners on individual child elements. When an event occurs, it bubbles up to the parent element, where the event listener handles it. This approach is efficient for managing events on dynamically created or large numbers of elements, reducing memory usage and improving performance.

**Example:**
```html
<ul id="parent">
  <li>Item 1</li>
  <li>Item 2</li>
</ul>

<script>
  document.getElementById("parent").addEventListener("click", (e) => {
    if (e.target.tagName === "LI") {
      console.log(`Clicked on: ${e.target.textContent}`);
    }
  });
</script>
```

---

### **Q15. How do you handle errors in JavaScript?**
**Answer:**  
Errors in JavaScript can be handled using `try...catch` statements. The `try` block contains the code that may throw an error, while the `catch` block handles the error if one occurs. Additionally, the `finally` block can be used to execute code regardless of whether an error occurs. Error objects provide information about the type and message of the error, allowing for customized error handling based on specific conditions.

**Example:**
```javascript
try {
  throw new Error("Something went wrong");
} catch (error) {
  console.log(error.message); // Output: Something went wrong
} finally {
  console.log("Execution complete");
}
```

---

### **Q16. What is the difference between synchronous and asynchronous programming in JavaScript?**
**Answer:**  
- Synchronous programming in JavaScript involves executing code sequentially, where each operation waits for the previous one to complete before executing.
- Asynchronous programming allows multiple operations to run concurrently, without waiting for each other to finish. Asynchronous operations use callbacks, promises, or `async/await` syntax to manage asynchronous code execution and handle results.

**Example:**
```javascript
// Synchronous
console.log("First");
console.log("Second");

// Asynchronous
setTimeout(() => console.log("Async"), 1000);
console.log("After setTimeout");
```

---

### **Q17. What are callback functions in JavaScript?**
**Answer:**  
Callback functions in JavaScript are functions passed as arguments to other functions, which are then invoked or executed at a later time, typically after an asynchronous operation has completed. They allow for asynchronous programming and event handling, enabling code execution to continue while waiting for time-consuming tasks to finish.

**Example:**
```javascript
function fetchData(callback) {
  setTimeout(() => callback("Data received"), 1000);
}

fetchData((data) => console.log(data)); // Output: Data received
```

---

### **Q18. How do you handle asynchronous operations in JavaScript?**
**Answer:**  
Asynchronous operations in JavaScript can be handled using callback functions, promises, or `async/await` syntax. Callback functions are passed as arguments to functions and executed once an operation completes. Promises provide a cleaner and more structured way to manage asynchronous code, allowing chaining of `then` and `catch` methods to handle success and error conditions. `Async/await` is a modern syntax that allows writing asynchronous code in a synchronous style, making it easier to read and understand.

**Example:**
```javascript
// Using Promises
fetch("https://api.example.com/data")
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error(error));

// Using async/await
async function getData() {
  try {
    const response = await fetch("https://api.example.com/data");
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}
getData();
```

---

### **Q19. Explain the concept of event loop in JavaScript.**
**Answer:**  
The event loop is a mechanism in JavaScript that handles asynchronous operations by continuously monitoring the call stack and message queue. It ensures that asynchronous tasks, such as callbacks and timers, are executed in the appropriate order and at the right time, preventing blocking of the main thread and ensuring smooth and responsive user experience.

**Example:**
```javascript
console.log("Start");

setTimeout(() => console.log("Timeout"), 0);

Promise.resolve().then(() => console.log("Promise"));

console.log("End");

// Output:
// Start
// End
// Promise
// Timeout
```

---

### **Q20. What is the purpose of the module pattern in JavaScript?**
**Answer:**  
The module pattern is a design pattern used to encapsulate and organize code into reusable modules with private and public members. It helps to avoid global namespace pollution and provides a clean and modular structure for organizing code. Modules can be created using immediately invoked function expressions (IIFE) to create a private scope, allowing for data encapsulation and abstraction.

**Example:**
```javascript
const Module = (() => {
  let privateVar = "I am private";

  return {
    getVar: () => privateVar,
    setVar: (value) => privateVar = value
  };
})();

console.log(Module.getVar()); // Output: I am private
Module.setVar("Updated");
console.log(Module.getVar()); // Output: Updated
```

---

### **Q21. What are the differences between ES5 and ES6?**
**Answer:**  
ES5 (ECMAScript 5) and ES6 (ECMAScript 2015) are two versions of the ECMAScript specification, the standard on which JavaScript is based. ES6 introduced several new features and syntax enhancements, including arrow functions, classes, template literals, `let` and `const` keywords, destructuring assignment, and modules. These additions improve code readability, maintainability, and developer productivity, making ES6 a significant advancement over ES5.

**Example:**
```javascript
// ES5
var name = "John";
function greet() {
  console.log("Hello, " + name);
}

// ES6
const name = "John";
const greet = () => console.log(`Hello, ${name}`);
```

---

### **Q22. What are the benefits of using strict mode in JavaScript?**
**Answer:**  
Strict mode is a feature introduced in ES5 that enables a stricter set of rules and error-checking mechanisms in JavaScript. It helps identify and eliminate common programming errors by enforcing best practices and preventing certain actions that can lead to silent errors or unexpected behavior. Benefits of using strict mode include improved code quality, better debugging capabilities, and enhanced security.

**Example:**
```javascript
"use strict";
x = 10; // Error: x is not defined
```

---

### **Q23. How do you implement inheritance in JavaScript?**
**Answer:**  
Inheritance in JavaScript is implemented using prototypal inheritance, where objects inherit properties and methods from their prototype object. Constructors and prototypes are used to define the inheritance hierarchy, with child objects inheriting from parent objects. `Object.create()` and `Object.setPrototypeOf()` methods can be used to establish prototype chains and set the prototype of an object to another object, enabling inheritance in JavaScript.

**Example:**
```javascript
class Parent {
  greet() {
    console.log("Hello from Parent");
  }
}

class Child extends Parent {
  greet() {
    super.greet();
    console.log("Hello from Child");
  }
}

const obj = new Child();
obj.greet();
```

---

### **Q24. What is the purpose of the fetch API in JavaScript?**
**Answer:**  
The fetch API is a modern JavaScript API for making asynchronous HTTP requests in the browser and Node.js environments. It provides a more powerful and flexible alternative to traditional XMLHttpRequest (XHR) for fetching resources from the network. The `fetch()` function returns a Promise that resolves to the response object, allowing for easier handling of HTTP requests and responses using `async/await` syntax or promise chaining.

**Example:**
```javascript
fetch("https://api.example.com/data")
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error(error));
```

---

### **Q25. How do you handle cross-origin requests in JavaScript?**
**Answer:**  
Cross-origin requests in JavaScript are handled using techniques like Cross-Origin Resource Sharing (CORS), JSONP (JSON with Padding), or proxy servers. CORS is a standard mechanism that allows servers to specify which origins are allowed to access their resources, while JSONP is a workaround that enables cross-origin requests by dynamically inserting script tags into the DOM. Proxy servers can be used to forward requests to remote servers, bypassing same-origin policy restrictions.

**Example:**
```javascript
// Using CORS
fetch("https://api.example.com/data", {
  method: "GET",
  headers: {
    "Content-Type": "application/json"
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error(error));
```

---

```
