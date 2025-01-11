

```markdown
# JavaScript Concepts with Examples

---

## 1. **`bind`, `call`, and `apply` Methods**
**Question:** What is the purpose of the `bind`, `call`, and `apply` methods?

**Answer:** These methods are used to control the value of the `this` keyword when calling a function. `bind` creates a new function with a fixed `this` value. `call` and `apply` immediately invoke the function with the provided `this` value and arguments.

**Example:**
```javascript
const person = {
    name: "Alice",
    greet: function() {
        console.log(`Hello, ${this.name}`);
    }
};

const greetFunc = person.greet.bind({ name: "Bob" }); // Bind
greetFunc(); // Hello, Bob

person.greet.call({ name: "Charlie" }); // Call
person.greet.apply({ name: "Dave" }); // Apply
```

---

## 2. **Callback Hell**
**Question:** What is ‘callback hell’ in the context of using callbacks, and what are its disadvantages?

**Answer:** “Callback hell” occurs when you have many nested callbacks in your code. It makes the code hard to read, debug, and maintain.

**Example:**
```javascript
getData(function(response1) {
    processData(response1, function(response2) {
        saveData(response2, function(response3) {
            displayData(response3, function(response4) {
                // More nested callbacks...
            });
        });
    });
});
```

---

## 3. **Promises**
**Question:** How is a Promise different from a callback, and what are the three states of a Promise?

**Answer:** Promises improve upon callbacks by offering better readability and error handling. A Promise can be in one of three states: **pending**, **fulfilled**, or **rejected**.

**Example:**
```javascript
const fetchData = new Promise((resolve, reject) => {
    setTimeout(() => {
        const data = "Fetched data";
        if (data) resolve(data); // Fulfilled
        else reject("Error fetching data"); // Rejected
    }, 1000);
});

fetchData
    .then((data) => console.log(data)) // Fulfilled state
    .catch((error) => console.error(error)); // Rejected state
```

---

## 4. **Async/Await**
**Question:** How does `async/await` help in writing asynchronous code?

**Answer:** `async/await` makes asynchronous code look like synchronous code, improving readability and maintainability.

**Example:**
```javascript
async function fetchData() {
    try {
        const response = await fetch("https://api.example.com/data");
        const data = await response.json();
        console.log(data);
    } catch (error) {
        console.error("Error:", error);
    }
}
fetchData();
```

---

## 5. **Map, Filter, Reduce**
**Question:** Briefly overview the `map`, `filter`, and `reduce` methods.

**Answer:**
- **`map`:** Transforms each element in an array.
- **`filter`:** Returns a new array with elements that pass a condition.
- **`reduce`:** Reduces an array to a single value.

**Example:**
```javascript
const numbers = [1, 2, 3, 4];

// Map: Transform each element
const squared = numbers.map(x => x * x); // [1, 4, 9, 16]

// Filter: Select elements that pass a condition
const evens = numbers.filter(x => x % 2 === 0); // [2, 4]

// Reduce: Accumulate values into a single result
const sum = numbers.reduce((acc, x) => acc + x, 0); // 10
```

---

## 6. **Closures**
**Question:** What is a closure, and how can it be used to create private data?

**Answer:** A closure is a function that "remembers" its outer scope, enabling data hiding and encapsulation.

**Example:**
```javascript
function createCounter() {
    let count = 0; // Private variable
    return function() {
        count++;
        return count;
    };
}

const counter = createCounter();
console.log(counter()); // 1
console.log(counter()); // 2
```

---

## 7. **Prototypal Inheritance**
**Question:** How does inheritance work in JavaScript?

**Answer:** In JavaScript, objects can inherit properties from other objects through prototypal inheritance.

**Example:**
```javascript
function Animal(name) {
    this.name = name;
}
Animal.prototype.speak = function() {
    console.log(`${this.name} makes a sound`);
};

function Dog(name) {
    Animal.call(this, name);
}
Dog.prototype = Object.create(Animal.prototype);

const dog = new Dog("Rex");
dog.speak(); // Rex makes a sound
```

---

## 8. **Destructuring**
**Question:** What is destructuring in JavaScript, and how is it useful?

**Answer:** Destructuring lets you unpack values from arrays or objects into distinct variables.

**Example:**
```javascript
const person = { name: "Alice", age: 25 };
const { name, age } = person; // Destructuring
console.log(name, age); // Alice 25
```

---

## 9. **Spread and Rest Operators**
**Question:** How do the spread and rest operators differ in JavaScript?

**Answer:**
- **Spread:** Unfolds elements.
- **Rest:** Gathers elements into an array or object.

**Example:**
```javascript
// Spread: Unfolds elements
const arr1 = [1, 2, 3];
const arr2 = [...arr1, 4, 5]; // [1, 2, 3, 4, 5]

// Rest: Gathers elements
function sum(...numbers) {
    return numbers.reduce((acc, x) => acc + x, 0);
}
console.log(sum(1, 2, 3)); // 6
```

---

## 10. **Try-Catch Block**
**Question:** How does the `try-catch` block help in handling exceptions in JavaScript?

**Answer:** The `try-catch` block allows developers to test a block of code for errors without crashing the application.

**Example:**
```javascript
try {
    throw new Error("This is a custom error");
} catch (error) {
    console.error(error.message); // This is a custom error
}
```

---

## 11. **Event Delegation**
**Question:** Why is event delegation beneficial, and how does it work?

**Answer:** Event delegation allows setting an event listener on a parent element rather than individual child elements. It improves performance and works with dynamically added elements.

**Example:**
```javascript
document.querySelector("#parent").addEventListener("click", (event) => {
    if (event.target.matches("button")) {
        console.log("Button clicked:", event.target.textContent);
    }
});
```

---

## 12. **Import/Export**
**Question:** How can you use the `import` and `export` statements in ES6?

**Answer:** ES6 modules allow breaking code into reusable pieces.

**Example:**
```javascript
// math.js
export const add = (a, b) => a + b;

// main.js
import { add } from "./math.js";
console.log(add(2, 3)); // 5
```

---

## 13. **Throttling and Debouncing**
**Question:** What are throttling and debouncing, and why are they essential in event handling?

**Answer:**
- **Throttling:** Limits how often a function can run.
- **Debouncing:** Delays a function until after a certain time has passed.

**Example:**
```javascript
// Throttling: Run once every 100ms
function throttle(func, limit) {
    let inThrottle;
    return function() {
        if (!inThrottle) {
            func.apply(this, arguments);
            inThrottle = true;
            setTimeout(() => inThrottle = false, limit);
        }
    };
}

// Debouncing: Run after 100ms of inactivity
function debounce(func, delay) {
    let timeout;
    return function() {
        clearTimeout(timeout);
        timeout = setTimeout(() => func.apply(this, arguments), delay);
    };
}
```

---

## 14. **LocalStorage vs SessionStorage**
**Question:** How do `localStorage` and `sessionStorage` differ?

**Answer:**
- **`localStorage`:** Persists data even after the browser is closed.
- **`sessionStorage`:** Clears data when the session ends.

**Example:**
```javascript
// localStorage
localStorage.setItem("name", "Alice");
console.log(localStorage.getItem("name")); // Alice

// sessionStorage
sessionStorage.setItem("name", "Bob");
console.log(sessionStorage.getItem("name")); // Bob
```

---

## 15. **JavaScript Engines**
**Question:** What is a JavaScript engine, and can you name a few popular ones?

**Answer:** A JavaScript engine translates code into machine language. Popular engines include:
- **V8:** Used in Chrome and Node.js.
- **SpiderMonkey:** Used in Firefox.
- **Chakra:** Used in Edge (legacy).
```
