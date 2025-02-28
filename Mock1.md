
### **JavaScript Concepts**

1. **What is a Pure and Impure Function?**  
   - **Pure Function:** Always produces the same output for the same input and has no side effects.  
   - **Impure Function:** May produce different outputs for the same input and has side effects (e.g., modifying global variables).  
   ```js
   function pureFunction(x, y) {
       return x + y; // Always returns the same output for the same inputs
   }
   
   let total = 0;
   function impureFunction(x) {
       total += x; // Modifies external state (side effect)
       return total;
   }
   ```

2. **What is Function Currying?**  
   - Currying transforms a function that takes multiple arguments into a sequence of functions, each taking a single argument.  
   ```js
   function curry(a) {
       return function (b) {
           return function (c) {
               return a + b + c;
           };
       };
   }
   console.log(curry(2)(3)(4)); // Output: 9
   ```

3. **Lexical Scope in JavaScript**  
   - Lexical scope means that a function's scope is determined by where it is defined, not where it is called.  
   ```js
   function outer() {
       let outerVar = "I'm outer";
       function inner() {
           console.log(outerVar); // Can access outer function's variable
       }
       inner();
   }
   outer();
   ```

4. **Different Array Methods**
   ```js
   let arr = [1, 2, 3, 4, 5];

   let mappedArr = arr.map(x => x * 2);  // [2, 4, 6, 8, 10]
   let reducedSum = arr.reduce((acc, val) => acc + val, 0); // 15
   let filteredArr = arr.filter(x => x > 2); // [3, 4, 5]
   ```

5. **Difference between Deep Copy and Shallow Copy**
   - **Shallow Copy:** Copies reference, changes affect the original object.
   - **Deep Copy:** Creates a completely new object.  
   ```js
   let obj1 = { a: 10, b: { c: 20 } };
   let shallowCopy = { ...obj1 }; // Changes in obj1.b will affect shallowCopy.b

   let deepCopy = JSON.parse(JSON.stringify(obj1)); // Creates a deep copy
   ```

6. **Different Pop-up Boxes**
   ```js
   alert("This is an alert"); // Simple message
   confirm("Are you sure?"); // OK/Cancel
   prompt("Enter your name"); // Input box
   ```

7. **Check if an Array Contains a Value**
   ```js
   let arr = [10, 20, 30];
   console.log(arr.includes(20)); // true
   ```

8. **Sorting an Array in Ascending Order**
   ```js
   let arr = [300, 8, 900, 400, 6];
   arr.sort((a, b) => a - b);
   console.log(arr); // [6, 8, 300, 400, 900]
   ```

9. **Strict Mode in JavaScript**
   - Helps catch errors by enforcing stricter parsing and error handling.  
   ```js
   "use strict";
   a = 10; // Error: a is not defined
   ```

10. **Promise Chaining**
    ```js
    new Promise((resolve, reject) => {
        setTimeout(() => resolve(10), 1000);
    }).then(value => {
        console.log(value);
        return value * 2;
    }).then(value => {
        console.log(value);
    });
    ```

11. **Event Loop in JavaScript**
    - The event loop allows JavaScript to handle asynchronous operations without blocking the main thread.
    ```js
    console.log("Start");

    setTimeout(() => console.log("Inside Timeout"), 0);

    console.log("End");
    ```

---

### **HTML and CSS Concepts**

12. **Difference between `<figure>` and `<img>`**
    - `<figure>` is a semantic container for images with captions.
    ```html
    <figure>
        <img src="image.jpg" alt="Description">
        <figcaption>This is an image caption</figcaption>
    </figure>
    ```

13. **Difference between Void and Empty Elements**
    - **Void Elements:** Do not have closing tags (e.g., `<br>`, `<img>`, `<input>`).  
    - **Empty Elements:** Have opening and closing tags but contain no content.

14. **Inline vs Block-Level Elements**
    - **Inline Elements:** Do not start a new line and only take up necessary space (e.g., `<span>`, `<a>`).  
    - **Block-Level Elements:** Start a new line and take up the full width (e.g., `<div>`, `<p>`).

15. **Different Types of Lists**
    ```html
    <ul> <!-- Unordered List -->
        <li>Item 1</li>
    </ul>

    <ol> <!-- Ordered List -->
        <li>Item 1</li>
    </ol>

    <dl> <!-- Description List -->
        <dt>Term</dt>
        <dd>Definition</dd>
    </dl>
    ```

16. **How to Create Multicolor Text**
    ```html
    <p style="color: red;">Red</p>
    <p style="color: blue;">Blue</p>
    ```

17. **Use of `alt` Attribute in `<img>`**
    - Provides alternate text for images, improving accessibility.
    ```html
    <img src="image.jpg" alt="A beautiful scenery">
    ```

18. **CSS Pseudo-Classes**
    ```css
    a:hover { color: red; } /* Changes color when hovered */
    input:focus { border: 2px solid blue; } /* Changes border when focused */
    ```

19. **CSS Keyframes for Animations**
    ```css
    @keyframes slide {
        0% { transform: translateX(0); }
        100% { transform: translateX(100px); }
    }

    div {
        animation: slide 2s infinite;
    }
    ```

---

These are the solutions to your questions. Let me know if you need further explanations! 🚀





### **1. HTML vs. HTML5 Differences**  
- **HTML:** Static, lacks support for modern features.  
- **HTML5:** Supports multimedia (audio, video), semantic elements (`<article>`, `<section>`), and better form controls.  

---

### **2. Box Model (Content, Margin, Border, Padding Differences)**  
- **Content:** Actual text/image inside the box.  
- **Padding:** Space between content and border.  
- **Border:** Outline around the padding and content.  
- **Margin:** Space outside the border separating elements.  

---

### **3. Difference Between ID and Class (Priority)**  
- **ID (`#id`)**: Unique, higher specificity, used for single elements.  
- **Class (`.class`)**: Can be reused, lower specificity.  

Priority order: `!important` > Inline styles > ID selectors > Class selectors  

---

### **4. Difference Between `let`, `var`, `const`**  
| Feature    | `var` | `let` | `const` |
|------------|------|------|--------|
| Scope | Function | Block | Block |
| Hoisting | Yes | Yes | No |
| Reassignable | Yes | Yes | No |

---

### **5. What is Media Query? (`@media`)**  
Used for responsive design.  
Example:  
```css
@media (max-width: 600px) {
  body {
    background-color: lightblue;
  }
}
```

---

### **6. Callback Functions (When to Use?)**  
A function passed as an argument to another function. Used in **event handling, asynchronous operations** like API calls.  

Example:  
```js
function greet(name, callback) {
  console.log("Hello " + name);
  callback();
}
greet("Gagan", () => console.log("Callback executed!"));
```

---

### **7. What is a Promise?**  
Used for handling async operations.  
```js
let promise = new Promise((resolve, reject) => {
  setTimeout(() => resolve("Data received"), 2000);
});
promise.then((data) => console.log(data));
```

---

### **8. Event Loop & Execution Context**  
- **Global Execution Context:** Default context where JS code runs.  
- **Event Loop:** Handles async operations, moves completed tasks from callback queue to call stack.  

---

### **9. CSS Preprocessor (SASS, LESS)**  
They extend CSS with variables, functions, and mixins.  
Example (SASS):  
```scss
$primary-color: blue;
.button {
  background-color: $primary-color;
}
```

---

### **10. Git Commands**  
```bash
git status  # Check changes  
git add .  # Stage all changes  
git commit -m "Message"  # Commit changes  
git push origin main  # Push to repository  
```

---

### **11. Difference Between `null` and `undefined`**  
- `null`: Assigned value, means "empty".  
- `undefined`: Unassigned variable.  

Example:  
```js
let a;
console.log(a); // undefined
let b = null;
console.log(b); // null
```

---

### **12. ES6 Features**  
- **Arrow Functions**  
  ```js
  const add = (a, b) => a + b;
  ```
- **Hoisting**  
  Arrow functions are **not hoisted**.  
- **Template Strings**  
  ```js
  let name = "Gagan";
  console.log(`Hello, ${name}`);
  ```

---

### **13. What is a Closure?**  
A function that **remembers the scope** in which it was created.  

Example:  
```js
function outer() {
  let count = 0;
  return function inner() {
    count++;
    console.log(count);
  };
}
const increment = outer();
increment(); // 1
increment(); // 2
```

---

### **14. What is `this` Keyword?**  
- In **global scope**, `this` refers to `window`.  
- Inside an **object**, it refers to the object itself.  
- In **arrow functions**, `this` is lexically bound.  

Example:  
```js
const obj = {
  name: "Gagan",
  show() {
    console.log(this.name);
  }
};
obj.show(); // "Gagan"
```

---

### **15. What is React.js?**  
- **Library** for building UI.  
- Uses **components** and **JSX**.  
- **Fast** due to virtual DOM.  
- **Reusability** with functional components.  

---

### **16. React Lifecycle (Class & Functional Components)**  
#### **Class Component Lifecycle**  
- `componentDidMount()` → Runs after component mounts.  
- `componentDidUpdate()` → Runs after state/props change.  
- `componentWillUnmount()` → Cleanup before unmounting.  

#### **Functional Component (useEffect)**  
```js
useEffect(() => {
  console.log("Component mounted!");
  return () => console.log("Cleanup before unmounting");
}, []);
```

---

### **17. What is `ref` in React?**  
Used to reference DOM elements or store mutable values without causing re-renders.  

Example:  
```js
import { useRef, useEffect } from "react";
function InputComponent() {
  const inputRef = useRef(null);
  useEffect(() => inputRef.current.focus(), []);
  return <input ref={inputRef} />;
}
```

