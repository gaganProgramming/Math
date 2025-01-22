


### 1. **Basic Structure of HTML**  
   - HTML documents begin with a `<!DOCTYPE html>` declaration.  
   - Standard structure:  
     ```html
     <!DOCTYPE html>
     <html lang="en">
     <head>
       <meta charset="UTF-8">
       <meta name="viewport" content="width=device-width, initial-scale=1.0">
       <title>Document Title</title>
     </head>
     <body>
       <!-- Content goes here -->
     </body>
     </html>
     ```

---

### 2. **Headings, Paragraphs, and Links**  
   - **Headings**:  
     ```html
     <h1>Main Heading</h1>
     <h2>Sub-heading</h2>
     ```
   - **Paragraphs**:  
     ```html
     <p>This is a paragraph.</p>
     ```
   - **Links**:  
     ```html
     <a href="https://example.com">Click here</a>
     ```

---

### 3. **Images, Lists, and Tables**  
   - **Images**:  
     ```html
     <img src="image.jpg" alt="Description" />
     ```
   - **Lists**:  
     - Ordered:  
       ```html
       <ol>
         <li>First item</li>
         <li>Second item</li>
       </ol>
       ```
     - Unordered:  
       ```html
       <ul>
         <li>Item one</li>
         <li>Item two</li>
       </ul>
       ```
   - **Tables**:  
     ```html
     <table>
       <tr>
         <th>Header</th>
         <th>Header</th>
       </tr>
       <tr>
         <td>Data</td>
         <td>Data</td>
       </tr>
     </table>
     ```

---

### 4. **SEO and Core Web Vitals**  
   - **SEO**: Use meta tags, structured data, and semantic HTML to improve search engine visibility.  
     ```html
     <meta name="description" content="An example website." />
     ```
   - **Core Web Vitals**: Metrics like LCP, FID, and CLS for performance.  

---

### 5. **Forms and Input Tags**  
   - Basic form structure:  
     ```html
     <form action="/submit" method="post">
       <label for="name">Name:</label>
       <input type="text" id="name" name="name" required />
       <button type="submit">Submit</button>
     </form>
     ```

---

### 6. **Inline and Block Elements in HTML**  
   - **Inline**: Does not start on a new line (e.g., `<span>`, `<a>`, `<img>`).  
   - **Block**: Starts on a new line and takes up full width (e.g., `<div>`, `<p>`, `<h1>`).  

---

### 7. **ID and Class**  
   - **ID**: Unique identifier for a single element.  
     ```html
     <div id="unique">Content</div>
     ```
   - **Class**: Can be shared across multiple elements.  
     ```html
     <div class="shared">Content</div>
     ```

---

### 8. **Video, Audio, and Media in HTML**  
   - **Video**:  
     ```html
     <video controls>
       <source src="video.mp4" type="video/mp4">
     </video>
     ```
   - **Audio**:  
     ```html
     <audio controls>
       <source src="audio.mp3" type="audio/mp3">
     </audio>
     ```

---

### 9. **Semantic Tags in HTML**  
   - Tags that convey meaning:  
     ```html
     <header>Header content</header>
     <main>Main content</main>
     <footer>Footer content</footer>
     <article>Article content</article>
     ```

---

### 10. **Entities, Code Tag, and More**  
   - **Entities**: For special characters.  
     ```html
     &copy; &lt; &gt;
     ```
   - **Code Tag**: Display code snippets.  
     ```html
     <code>console.log("Hello World!");</code>
     ```  
   - **Other Useful Tags**:  
     ```html
     <abbr title="World Health Organization">WHO</abbr>
     <mark>Highlighted text</mark>
     <time datetime="2025-01-23">January 23, 2025</time>
     ```

### 1. **Inline, Internal & External CSS**  
   - **Inline CSS**: Add styles directly to an element using the `style` attribute.  
     ```html
     <p style="color: blue;">Hello, World!</p>
     ```
   - **Internal CSS**: Write CSS within a `<style>` tag in the `<head>`.  
     ```html
     <style>
       p { color: red; }
     </style>
     ```
   - **External CSS**: Use a separate `.css` file linked with a `<link>` tag.  
     ```html
     <link rel="stylesheet" href="styles.css">
     ```

---

### 2. **CSS Selectors**  
   - **Types**:  
     - Universal: `*`  
     - Element: `h1, p`  
     - Class: `.classname`  
     - ID: `#idname`  
     - Attribute: `[type="text"]`  
     - Pseudo-classes: `:hover`, `:nth-child()`.  

---

### 3. **CSS Box Model: Margin, Padding & Borders**  
   - **Content**: The inner text or image.  
   - **Padding**: Space between content and border.  
   - **Border**: Surrounds padding.  
   - **Margin**: Space outside the border.  
     ```css
     div {
       margin: 10px;
       padding: 20px;
       border: 2px solid black;
     }
     ```

---

### 4. **CSS Fonts, Text & Color Properties**  
   - Fonts: `font-family`, `font-size`, `font-weight`.  
   - Text: `text-align`, `text-transform`, `line-height`.  
   - Colors: `color`, `background-color`.  

---

### 5. **Specificity and Cascade**  
   - **Specificity**: Determines which CSS rule applies. Inline > ID > Class > Element.  
   - **Cascade**: Later rules overwrite earlier ones if equally specific.  

---

### 6. **Sizing Units**  
   - `px`: Absolute pixels.  
   - `rem`: Relative to the root font size.  
   - `em`: Relative to the parent element.  
   - `%`: Relative to the containing element.  
   - `vh`, `vw`: Viewport height and width.  

---

### 7. **Display Property**  
   - `block`, `inline`, `inline-block`, `none`, `flex`, `grid`.  
     ```css
     div {
       display: flex;
     }
     ```

---

### 8. **Shadows and Outlines**  
   - Box Shadow:
     ```css
     box-shadow: 2px 2px 5px gray;
     ```
   - Text Shadow:
     ```css
     text-shadow: 1px 1px 2px black;
     ```

---

### 9. **Styling Lists**  
   - Customize bullet points or numbers with `list-style`.  
     ```css
     ul {
       list-style: square;
     }
     ```

---

### 10. **Overflow Property**  
   - Controls content overflowing an element.  
     - `visible`, `hidden`, `scroll`, `auto`.  

---

### 11. **Position Property**  
   - Types: `static`, `relative`, `absolute`, `fixed`, `sticky`.  
     ```css
     div {
       position: absolute;
       top: 50px;
       left: 100px;
     }
     ```

---

### 12. **Design This Card**  
   - A basic card structure:
     ```css
     .card {
       width: 300px;
       padding: 20px;
       border: 1px solid #ccc;
       box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
       border-radius: 10px;
     }
     ```

---

### 13. **CSS Variables**  
   - Define reusable variables with `--`.  
     ```css
     :root {
       --primary-color: blue;
     }
     h1 {
       color: var(--primary-color);
     }
     ```

---

### 14. **Media Queries**  
   - Make designs responsive:
     ```css
     @media (max-width: 600px) {
       body {
         font-size: 14px;
       }
     }
     ```

---

### 15. **Float and Clear**  
   - Float: Align elements.
     ```css
     img {
       float: left;
     }
     ```
   - Clear: Prevent overlap.
     ```css
     div {
       clear: both;
     }
     ```

---

### 16. **Flexbox**  
   - Layout module for alignment.
     ```css
     .container {
       display: flex;
       justify-content: center;
       align-items: center;
     }
     ```

---

### 17. **Grid**  
   - Two-dimensional layout.
     ```css
     .grid {
       display: grid;
       grid-template-columns: repeat(3, 1fr);
       gap: 10px;
     }
     ```

---

### 18. **Transition Property**  
   - Add smooth changes.
     ```css
     button {
       transition: background-color 0.3s ease;
     }
     ```

---

### 19. **Animations in CSS**  
   - Create keyframes and animations:
     ```css
     @keyframes move {
       from {
         transform: translateX(0);
       }
       to {
         transform: translateX(100px);
       }
     }
     div {
       animation: move 2s infinite;
     }
     ```

---

### 20. **Object-Fit and Object-Cover**  
   - Fit media in containers.
     ```css
     img {
       object-fit: cover;
     }
     ```

---

### 21. **Filters**  
   - Apply effects like blur or grayscale.
     ```css
     img {
       filter: grayscale(100%);
     }
     ```

---

### 22. **Figma Basics**  
   - A design tool for creating UI mockups.  
     - Features: Frames, Components, Prototypes, and Design Grids.  
     - Allows collaboration and exporting designs for development.  



### 1. **JavaScript Variables, Datatypes, and Objects**  
   - **Variables**: Declare using `var`, `let`, or `const`.  
     ```javascript
     let name = "John";
     const age = 25;
     var city = "New York";
     ```
   - **Datatypes**:  
     - Primitive: `String`, `Number`, `Boolean`, `null`, `undefined`, `Symbol`, `BigInt`.  
     - Non-Primitive: `Object`, `Array`, `Function`.  
   - **Objects**: Key-value pairs.
     ```javascript
     const person = { name: "Alice", age: 30, city: "Paris" };
     ```

---

### 2. **JavaScript Conditionals: `if`, `else if`, `else` Ladder**  
   - Used for decision-making.
     ```javascript
     let age = 18;
     if (age < 13) {
       console.log("Child");
     } else if (age >= 13 && age < 18) {
       console.log("Teenager");
     } else {
       console.log("Adult");
     }
     ```

---

### 3. **JavaScript Loops**  
   - **For Loop**:
     ```javascript
     for (let i = 0; i < 5; i++) {
       console.log(i);
     }
     ```
   - **While Loop**:
     ```javascript
     let i = 0;
     while (i < 5) {
       console.log(i++);
     }
     ```
   - **Do-While Loop**:
     ```javascript
     let i = 0;
     do {
       console.log(i++);
     } while (i < 5);
     ```

---

### 4. **JavaScript Functions**  
   - **Function Declaration**:
     ```javascript
     function greet(name) {
       return `Hello, ${name}`;
     }
     ```
   - **Function Expression**:
     ```javascript
     const greet = function (name) {
       return `Hello, ${name}`;
     };
     ```
   - **Arrow Functions**:
     ```javascript
     const greet = (name) => `Hello, ${name}`;
     ```

---

### 5. **JavaScript Strings**  
   - Methods: `length`, `toUpperCase()`, `toLowerCase()`, `slice()`, `substring()`, `replace()`.  
     ```javascript
     const str = "JavaScript";
     console.log(str.toUpperCase());
     console.log(str.slice(0, 4));
     ```

---

### 6. **JavaScript Arrays**  
   - Methods: `push()`, `pop()`, `shift()`, `unshift()`, `map()`, `filter()`, `reduce()`.  
     ```javascript
     const arr = [1, 2, 3, 4];
     arr.push(5); // [1, 2, 3, 4, 5]
     ```

---

### 7. **Document Object Model (DOM) in JavaScript**  
   - Interface for interacting with the HTML structure.
     ```javascript
     document.title = "New Title";
     document.body.style.backgroundColor = "lightblue";
     ```

---

### 8. **JavaScript DOM - Children, Parent & Sibling Nodes**  
   - **Children**: Access child elements.
     ```javascript
     const parent = document.getElementById("parent");
     const children = parent.children;
     ```
   - **Parent**: Access parent node.
     ```javascript
     const child = document.getElementById("child");
     const parent = child.parentNode;
     ```
   - **Siblings**: Navigate sibling elements.
     ```javascript
     const next = child.nextElementSibling;
     const previous = child.previousElementSibling;
     ```

---

### 9. **JavaScript - Selecting by IDs, Classes, and More**  
   - `getElementById`, `getElementsByClassName`, `querySelector`, `querySelectorAll`.  
     ```javascript
     document.getElementById("myId");
     document.querySelector(".myClass");
     ```

---

### 10. **Inserting and Removing Elements Using JavaScript**  
   - **Inserting**:
     ```javascript
     const newElement = document.createElement("div");
     document.body.appendChild(newElement);
     ```
   - **Removing**:
     ```javascript
     const element = document.getElementById("removeMe");
     element.remove();
     ```

---

### 11. **Events, Event Bubbling, `setInterval` & `setTimeout`**  
   - **Events**:
     ```javascript
     document.addEventListener("click", () => alert("Clicked!"));
     ```
   - **Event Bubbling**: Events propagate upward.
   - **`setTimeout`**:
     ```javascript
     setTimeout(() => console.log("Delayed"), 1000);
     ```
   - **`setInterval`**:
     ```javascript
     setInterval(() => console.log("Repeats"), 1000);
     ```

---

### 12. **JavaScript Callbacks & Promises**  
   - **Callbacks**:
     ```javascript
     function doTask(callback) {
       setTimeout(() => {
         callback("Task Complete");
       }, 1000);
     }
     ```
   - **Promises**:
     ```javascript
     const promise = new Promise((resolve, reject) => {
       resolve("Success");
     });
     ```

---

### 13. **Async/Await & Fetch API in JavaScript with Examples**  
   - **Fetch API**:
     ```javascript
     fetch("https://api.example.com/data")
       .then((response) => response.json())
       .then((data) => console.log(data));
     ```
   - **Async/Await**:
     ```javascript
     async function fetchData() {
       const response = await fetch("https://api.example.com/data");
       const data = await response.json();
       console.log(data);
     }
     ```

---

### 14. **JavaScript `try...catch` & Error Handling**  
   - Handle errors gracefully.
     ```javascript
     try {
       throw new Error("Something went wrong");
     } catch (error) {
       console.error(error.message);
     }
     ```

---

### 15. **Classes & Objects - OOP in JavaScript**  
   - Define classes and objects.
     ```javascript
     class Person {
       constructor(name, age) {
         this.name = name;
         this.age = age;
       }
       greet() {
         console.log(`Hi, I'm ${this.name}`);
       }
     }
     ```

---

### 16. **Advanced JavaScript**  
   - Topics include closures, `this`, prototypal inheritance, modules, and higher-order functions.
     ```javascript
     function outer() {
       let count = 0;
       return function inner() {
         count++;
         return count;
       };
     }
     const counter = outer();
     console.log(counter()); // 1
     ```









     ### 1. **Introduction to React and Why Use React?**  
   React is a JavaScript library for building user interfaces, developed by Facebook.  
   **Why Use React?**
   - **Component-Based**: Build reusable UI components.
   - **Virtual DOM**: Faster updates by only changing necessary parts of the DOM.
   - **Unidirectional Data Flow**: Predictable and manageable state.
   - **React Ecosystem**: Hooks, React Router, and tools like Redux.
   - **Rich Developer Tools**: Extensions for debugging.

---

### 2. **Components, Props, and JSX in React**  
   - **Components**: Building blocks of a React app. They can be functional or class-based.  
     ```jsx
     function Greeting() {
       return <h1>Hello, World!</h1>;
     }
     ```
   - **Props**: Pass data to components as arguments.
     ```jsx
     function Greeting({ name }) {
       return <h1>Hello, {name}!</h1>;
     }
     ```
   - **JSX**: Syntax extension for writing HTML in JavaScript.
     ```jsx
     const element = <h1>Hello, JSX!</h1>;
     ```

---

### 3. **Hooks and State in React**  
   - **State**: Allows components to manage data.
     ```jsx
     import { useState } from 'react';

     function Counter() {
       const [count, setCount] = useState(0);
       return <button onClick={() => setCount(count + 1)}>Count: {count}</button>;
     }
     ```
   - **Hooks**: Functions that let you use state and lifecycle features in functional components.

---

### 4. **The `useEffect` Hook in React**  
   - Used for side effects (e.g., fetching data, subscriptions).  
     ```jsx
     import { useEffect } from 'react';

     useEffect(() => {
       console.log('Component mounted');
       return () => console.log('Component unmounted');
     }, []);
     ```

---

### 5. **The `useRef` Hook in React**  
   - Creates a mutable reference to access DOM elements or persist data between renders.  
     ```jsx
     import { useRef } from 'react';

     function InputFocus() {
       const inputRef = useRef();
       return (
         <div>
           <input ref={inputRef} />
           <button onClick={() => inputRef.current.focus()}>Focus</button>
         </div>
       );
     }
     ```

---

### 6. **Conditional Rendering and Rendering Lists in React**  
   - **Conditional Rendering**:
     ```jsx
     function App({ isLoggedIn }) {
       return isLoggedIn ? <h1>Welcome</h1> : <h1>Please Login</h1>;
     }
     ```
   - **Rendering Lists**:
     ```jsx
     const items = ['Apple', 'Banana', 'Cherry'];
     const list = items.map((item, index) => <li key={index}>{item}</li>);
     ```

---

### 7. **Handling Events in React**  
   - Handle events using JavaScript functions:
     ```jsx
     function App() {
       function handleClick() {
         alert('Button clicked!');
       }
       return <button onClick={handleClick}>Click Me</button>;
     }
     ```

---

### 8. **React Router**  
   Enables navigation between pages without full-page reloads.  
   - Installation: `npm install react-router-dom`  
   - Example:
     ```jsx
     import { BrowserRouter, Route, Routes, Link } from 'react-router-dom';

     function App() {
       return (
         <BrowserRouter>
           <nav>
             <Link to="/">Home</Link>
             <Link to="/about">About</Link>
           </nav>
           <Routes>
             <Route path="/" element={<Home />} />
             <Route path="/about" element={<About />} />
           </Routes>
         </BrowserRouter>
       );
     }
     ```

---

### 9. **The `useContext` Hook in React**  
   - Shares state between components without props drilling.
     ```jsx
     import { createContext, useContext } from 'react';

     const ThemeContext = createContext('light');
     function ThemeButton() {
       const theme = useContext(ThemeContext);
       return <button>{theme}</button>;
     }
     ```

---

### 10. **The `useMemo` Hook in React**  
   - Memoizes the result of expensive computations.
     ```jsx
     import { useMemo } from 'react';

     const result = useMemo(() => computeExpensiveValue(a, b), [a, b]);
     ```

---

### 11. **The `useCallback` Hook in React**  
   - Memoizes a callback function to avoid unnecessary re-creations.
     ```jsx
     import { useCallback } from 'react';

     const memoizedCallback = useCallback(() => doSomething(a, b), [a, b]);
     ```

---

### 12. **Handling Forms + Connecting React to Express Backend**  
   - **Forms**:
     ```jsx
     function Form() {
       const [value, setValue] = useState('');
       const handleSubmit = (e) => {
         e.preventDefault();
         console.log(value);
       };
       return (
         <form onSubmit={handleSubmit}>
           <input value={value} onChange={(e) => setValue(e.target.value)} />
           <button type="submit">Submit</button>
         </form>
       );
     }
     ```
   - **Connecting to Express Backend**:
     ```js
     const handleSubmit = async () => {
       const response = await fetch('http://localhost:5000/api', {
         method: 'POST',
         headers: { 'Content-Type': 'application/json' },
         body: JSON.stringify({ data: value }),
       });
     };
     ```

---

### 13. **React Redux**  
   - State management library for global state in large applications.
   - Setup:
     ```bash
     npm install @reduxjs/toolkit react-redux
     ```
   - Example:
     ```js
     import { configureStore } from '@reduxjs/toolkit';
     import { Provider, useDispatch, useSelector } from 'react-redux';

     const store = configureStore({ reducer: { counter: counterReducer } });
     const Counter = () => {
       const dispatch = useDispatch();
       const count = useSelector((state) => state.counter);
       return (
         <button onClick={() => dispatch(increment())}>Count: {count}</button>
       );
     };
     ```












### 1. **Introduction to Next.js and File-Based Routing**  
   **Next.js** is a React framework for building server-rendered and statically generated applications. It simplifies development with features like pre-rendering, routing, and API integration.  
   - **File-Based Routing**: The `pages` directory defines the app's routes. Each file corresponds to a route. For example:
     - `pages/index.js` → `/`
     - `pages/about.js` → `/about`
   - Dynamic routes can be created using brackets, e.g., `pages/[id].js` handles `/post/1`.

---

### 2. **Server Components in Next.js**  
   Server components run on the server and send minimal HTML to the client, improving performance. Introduced in React 18 and supported by Next.js:  
   - **Benefits**: Reduced JavaScript on the client, better load times.
   - **Usage**: Default in Next.js under the `/app` directory. Files like `page.js` render server components.

---

### 3. **Script, Link, and Image Components in Next.js**  
   - **Script**: Optimizes third-party scripts with the `next/script` component. Example:
     ```jsx
     import Script from 'next/script';
     <Script src="https://example.com/script.js" strategy="lazyOnload" />
     ```
   - **Link**: Enhances navigation by prefetching with `next/link`. Example:
     ```jsx
     import Link from 'next/link';
     <Link href="/about">About</Link>
     ```
   - **Image**: Optimized image rendering with `next/image`. Example:
     ```jsx
     import Image from 'next/image';
     <Image src="/image.jpg" alt="Example" width={500} height={500} />
     ```

---

### 4. **Creating APIs in Next.js**  
   Next.js allows API routes under the `pages/api` directory:  
   - Example: `pages/api/hello.js`  
     ```js
     export default function handler(req, res) {
       res.status(200).json({ message: "Hello, world!" });
     }
     ```
   - These endpoints are serverless and auto-scalable.

---

### 5. **Server Actions in Next.js**  
   - Server actions simplify server-side data manipulation. You can mutate data directly on the server and call these actions from client components.
   - Example:
     ```js
     'use server';

     export async function saveData(formData) {
       // Server logic here
     }
     ```

---

### 6. **Middleware in Next.js**  
   Middleware intercepts requests and modifies responses. It runs before the request reaches the handler.  
   - Create in `middleware.js`:
     ```js
     export function middleware(request) {
       const url = request.nextUrl.clone();
       url.pathname = '/login';
       return NextResponse.redirect(url);
     }
     ```
   - Useful for authentication, redirects, and more.

---

### 7. **Auth.js - Authentication in Next.js**  
   `next-auth` is a library for authentication in Next.js:  
   - Install: `npm install next-auth`  
   - Add API route: `pages/api/auth/[...nextauth].js`  
   - Example:
     ```js
     import NextAuth from 'next-auth';
     import Providers from 'next-auth/providers';

     export default NextAuth({
       providers: [
         Providers.Google({
           clientId: process.env.GOOGLE_ID,
           clientSecret: process.env.GOOGLE_SECRET,
         }),
       ],
     });
     ```

---

### 8. **Dynamic Routes in Next.js**  
   Dynamic routes are created using brackets in filenames.  
   - Example: `pages/post/[id].js`
     ```js
     export default function Post({ params }) {
       return <h1>Post ID: {params.id}</h1>;
     }
     ```

---

### 9. **Layouts in Next.js**  
   Layouts provide reusable UI structure. In the `/app` directory, use `layout.js`:  
   - Example:
     ```jsx
     export default function RootLayout({ children }) {
       return (
         <html>
           <body>
             <header>Header</header>
             {children}
             <footer>Footer</footer>
           </body>
         </html>
       );
     }
     ```

---

### 10. **Understanding `next/navigation` Module in Next.js**  
   This module provides programmatic navigation.  
   - Example:
     ```jsx
     import { useRouter } from 'next/navigation';

     function HomePage() {
       const router = useRouter();
       return <button onClick={() => router.push('/about')}>Go to About</button>;
     }
     ```

---

### 11. **SSR, SSG, and ISR in Next.js**  
   - **SSR**: Server-Side Rendering (renders at request time).  
     ```js
     export async function getServerSideProps() {
       return { props: { data: 'Server Rendered' } };
     }
     ```
   - **SSG**: Static Site Generation (build-time rendering).  
     ```js
     export async function getStaticProps() {
       return { props: { data: 'Static Rendered' } };
     }
     ```
   - **ISR**: Incremental Static Regeneration (updates static content after build).  
     ```js
     export async function getStaticProps() {
       return { props: { data: 'ISR Rendered' }, revalidate: 10 };
     }
     ```

---

### 12. **Environment Variables in Next.js**  
   Store sensitive data in `.env.local`:  
   ```env
   NEXT_PUBLIC_API_URL=http://api.example.com
   ```
   Access in code:
   ```js
   const apiUrl = process.env.NEXT_PUBLIC_API_URL;
   ```

---

### 13. **Styled JSX and Other Ways to Style in Next.js**  
   - **Styled JSX**: Scoped CSS in components.
     ```jsx
     <style jsx>{`
       div {
         color: blue;
       }
     `}</style>
     ```
   - Other methods:
     - CSS Modules: `module.css`.
     - Tailwind CSS.
     - Styled-components.

---

### 14. **Deploying Next.js App**  
   - Platforms: **Vercel** (recommended), **Netlify**, or self-hosting.
   - Steps for Vercel:
     1. Connect your GitHub repository.
     2. Deploy directly with minimal setup.
   - Build: `npm run build`, then `npm start` for self-hosted.






     
