# Tasks
# React Tasks
-----------
In React interviews, tasks similar to the **counter program** focus on **state management, event handling, and component rendering**. Here are some common tasks:

---

### 🔹 **State & Event Handling Tasks**
1. **To-Do List App** – Add, remove, and mark tasks as completed using `useState`.
2. **Form Validation** – Validate user input (e.g., email, password) and show error messages.
3. **Stopwatch / Timer** – Implement a start/stop/reset timer using `useEffect` and `setInterval`.
4. **Like/Dislike Button** – Toggle between "Liked" and "Unliked" states.
5. **Dark Mode Toggle** – Implement a light/dark theme switch using local storage.

---

### 🔹 **API & Data Fetching Tasks**
6. **Fetch and Display Data** – Fetch user data from an API (e.g., JSONPlaceholder).
7. **Search & Filter List** – Filter a list of items dynamically as the user types.
8. **Debounced Search** – Optimize search input using **debounce** (`lodash.debounce` or `setTimeout`).
9. **Infinite Scrolling** – Load more data as the user scrolls down.
10. **Auto-Suggestions** – Display suggested items based on user input.

---

### 🔹 **React Component & State Management Tasks**
11. **Dynamic Table with Sorting** – Display data in a table with sorting (ascending/descending).
12. **Drag and Drop List** – Allow users to reorder list items (e.g., using `react-beautiful-dnd`).
13. **Accordion Component** – Expand/collapse sections dynamically.
14. **Multi-Step Form** – Implement a step-by-step form with navigation.
15. **Image Carousel** – Create a slideshow that auto-scrolls or changes on button click.

---

### 🔹 **React Hooks & Performance Tasks**
16. **Use Context API for Global State** – Manage user authentication state globally.
17. **UseReducer Instead of UseState** – Refactor a counter or form with `useReducer`.
18. **Lazy Loading Components** – Load heavy components only when needed (`React.lazy` + `Suspense`).
19. **Memoization with useMemo & useCallback** – Optimize performance in lists or expensive calculations.
20. **Custom Hook Creation** – Create a custom hook for fetching API data.

---

### 🔹 **Advanced React & Next.js Tasks**
21. **Protected Routes** – Restrict access to certain pages based on authentication.
22. **SSR vs CSR in Next.js** – Implement both Server-Side Rendering (`getServerSideProps`) and Client-Side Rendering.
23. **Pagination** – Implement a paginated list fetching API data.
24. **WebSockets with React** – Implement real-time chat using WebSockets (`socket.io`).
25. **Progressive Web App (PWA) Setup** – Convert a React app into a PWA.

---

# Solutions

Here are the solutions for **State & Event Handling Tasks** in React:

---

## **1️⃣ To-Do List App (Add, Remove, Complete)**
```jsx
import { useState } from "react";

export default function TodoApp() {
  const [tasks, setTasks] = useState([]);
  const [newTask, setNewTask] = useState("");

  const addTask = () => {
    if (!newTask.trim()) return;
    setTasks([...tasks, { id: Date.now(), text: newTask, completed: false }]);
    setNewTask("");
  };

  const toggleComplete = (id) => {
    setTasks(tasks.map(task => task.id === id ? { ...task, completed: !task.completed } : task));
  };

  const deleteTask = (id) => {
    setTasks(tasks.filter(task => task.id !== id));
  };

  return (
    <div>
      <input value={newTask} onChange={(e) => setNewTask(e.target.value)} placeholder="New Task" />
      <button onClick={addTask}>Add</button>
      <ul>
        {tasks.map(task => (
          <li key={task.id} onClick={() => toggleComplete(task.id)}>
            <span style={{ textDecoration: task.completed ? "line-through" : "none" }}>{task.text}</span>
            <button onClick={() => deleteTask(task.id)}>Delete</button>
          </li>
        ))}
      </ul>
    </div>
  );
}
```

---

## **2️⃣ Form Validation (Email & Password)**
```jsx
import { useState } from "react";

export default function FormValidation() {
  const [email, setEmail] = useState("");
  const [password, setPassword] = useState("");
  const [errors, setErrors] = useState({});

  const validate = () => {
    let errors = {};
    if (!email.includes("@")) errors.email = "Invalid email!";
    if (password.length < 6) errors.password = "Password too short!";
    setErrors(errors);
    return Object.keys(errors).length === 0;
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    if (validate()) alert("Form submitted!");
  };

  return (
    <form onSubmit={handleSubmit}>
      <input type="text" placeholder="Email" value={email} onChange={(e) => setEmail(e.target.value)} />
      {errors.email && <p>{errors.email}</p>}
      <input type="password" placeholder="Password" value={password} onChange={(e) => setPassword(e.target.value)} />
      {errors.password && <p>{errors.password}</p>}
      <button type="submit">Submit</button>
    </form>
  );
}
```

---

## **3️⃣ Stopwatch / Timer (Start, Stop, Reset)**
```jsx
import { useState, useEffect } from "react";

export default function Stopwatch() {
  const [time, setTime] = useState(0);
  const [isRunning, setIsRunning] = useState(false);

  useEffect(() => {
    let timer;
    if (isRunning) {
      timer = setInterval(() => setTime(prev => prev + 1), 1000);
    }
    return () => clearInterval(timer);
  }, [isRunning]);

  return (
    <div>
      <h1>{time}s</h1>
      <button onClick={() => setIsRunning(true)}>Start</button>
      <button onClick={() => setIsRunning(false)}>Stop</button>
      <button onClick={() => { setTime(0); setIsRunning(false); }}>Reset</button>
    </div>
  );
}
```

---

## **4️⃣ Like/Dislike Button**
```jsx
import { useState } from "react";

export default function LikeButton() {
  const [liked, setLiked] = useState(false);

  return (
    <button onClick={() => setLiked(!liked)}>
      {liked ? "❤️ Liked" : "🤍 Like"}
    </button>
  );
}
```

---

## **5️⃣ Dark Mode Toggle (Persist with Local Storage)**
```jsx
import { useState, useEffect } from "react";

export default function DarkModeToggle() {
  const [darkMode, setDarkMode] = useState(() => {
    return localStorage.getItem("darkMode") === "true";
  });

  useEffect(() => {
    localStorage.setItem("darkMode", darkMode);
  }, [darkMode]);

  return (
    <div style={{ backgroundColor: darkMode ? "#333" : "#fff", color: darkMode ? "#fff" : "#000", padding: "20px" }}>
      <button onClick={() => setDarkMode(!darkMode)}>Toggle Dark Mode</button>
    </div>
  );
}
```

---

✅ **These solutions cover:**
- `useState` for state management.
- `useEffect` for side effects (timer, local storage).
- **Event handling** (`onClick`, `onChange`).
- **Conditional rendering** (`? :` for toggling states).


Here are the **API & Data Fetching Task** solutions in React:

---

## **1️⃣ Fetch and Display Data (JSONPlaceholder API)**
```jsx
import { useState, useEffect } from "react";

export default function FetchUsers() {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/users")
      .then(response => response.json())
      .then(data => setUsers(data))
      .catch(error => console.error("Error fetching users:", error));
  }, []);

  return (
    <div>
      <h2>User List</h2>
      <ul>
        {users.map(user => (
          <li key={user.id}>{user.name} - {user.email}</li>
        ))}
      </ul>
    </div>
  );
}
```
✅ **Concepts Used:** `useEffect`, `fetch API`, `useState`

---

## **2️⃣ Search & Filter List (Live Search)**
```jsx
import { useState } from "react";

const items = ["Apple", "Banana", "Cherry", "Mango", "Pineapple", "Strawberry"];

export default function SearchFilter() {
  const [query, setQuery] = useState("");

  const filteredItems = items.filter(item => item.toLowerCase().includes(query.toLowerCase()));

  return (
    <div>
      <input type="text" placeholder="Search..." onChange={(e) => setQuery(e.target.value)} />
      <ul>
        {filteredItems.map((item, index) => <li key={index}>{item}</li>)}
      </ul>
    </div>
  );
}
```
✅ **Concepts Used:** `useState`, `filter()`, `toLowerCase()`

---

## **3️⃣ Debounced Search (Using `lodash.debounce`)**
```jsx
import { useState, useEffect } from "react";
import debounce from "lodash.debounce";

export default function DebouncedSearch() {
  const [query, setQuery] = useState("");
  const [results, setResults] = useState([]);

  const fetchResults = debounce(async (searchTerm) => {
    if (!searchTerm) return;
    const response = await fetch(`https://jsonplaceholder.typicode.com/users?q=${searchTerm}`);
    const data = await response.json();
    setResults(data);
  }, 500);

  useEffect(() => {
    fetchResults(query);
  }, [query]);

  return (
    <div>
      <input type="text" placeholder="Search..." onChange={(e) => setQuery(e.target.value)} />
      <ul>
        {results.map(user => <li key={user.id}>{user.name}</li>)}
      </ul>
    </div>
  );
}
```
✅ **Concepts Used:** `lodash.debounce`, `useEffect`, `fetch API`

---

## **4️⃣ Infinite Scrolling (Using `IntersectionObserver`)**
```jsx
import { useState, useEffect, useRef } from "react";

export default function InfiniteScroll() {
  const [posts, setPosts] = useState([]);
  const [page, setPage] = useState(1);
  const loader = useRef(null);

  useEffect(() => {
    fetch(`https://jsonplaceholder.typicode.com/posts?_limit=10&_page=${page}`)
      .then(res => res.json())
      .then(data => setPosts(prev => [...prev, ...data]))
      .catch(error => console.error("Error:", error));
  }, [page]);

  useEffect(() => {
    const observer = new IntersectionObserver(entries => {
      if (entries[0].isIntersecting) setPage(prev => prev + 1);
    }, { threshold: 1 });

    if (loader.current) observer.observe(loader.current);
    return () => observer.disconnect();
  }, []);

  return (
    <div>
      <h2>Posts</h2>
      {posts.map(post => (
        <p key={post.id}>{post.title}</p>
      ))}
      <div ref={loader}>Loading...</div>
    </div>
  );
}
```
✅ **Concepts Used:** `IntersectionObserver`, `useEffect`, `fetch API`

---

## **5️⃣ Auto-Suggestions (Type & Get Suggestions)**
```jsx
import { useState } from "react";

const items = ["Apple", "Banana", "Cherry", "Mango", "Pineapple", "Strawberry"];

export default function AutoSuggest() {
  const [query, setQuery] = useState("");
  const [suggestions, setSuggestions] = useState([]);

  const handleChange = (e) => {
    const value = e.target.value;
    setQuery(value);
    setSuggestions(items.filter(item => item.toLowerCase().includes(value.toLowerCase())));
  };

  return (
    <div>
      <input type="text" value={query} onChange={handleChange} placeholder="Type a fruit..." />
      {suggestions.length > 0 && (
        <ul>
          {suggestions.map((item, index) => <li key={index}>{item}</li>)}
        </ul>
      )}
    </div>
  );
}
```
✅ **Concepts Used:** `useState`, `filter()`

---

### **🔥 Summary**
| Task | Key Concept |
|-------|------------|
| Fetch Data | `fetch API`, `useEffect` |
| Search & Filter | `filter()`, `useState` |
| Debounced Search | `lodash.debounce`, `setTimeout()` |
| Infinite Scrolling | `IntersectionObserver`, `useEffect` |
| Auto-Suggestions | `useState`, `filter()` |

---

Here are the solutions for **Dynamic Table, Drag and Drop, Accordion, Multi-Step Form, and Image Carousel** in React:

---

## **1️⃣ Dynamic Table with Sorting**
```jsx
import { useState } from "react";

const data = [
  { id: 1, name: "Alice", age: 25 },
  { id: 2, name: "Bob", age: 30 },
  { id: 3, name: "Charlie", age: 22 },
];

export default function SortableTable() {
  const [sortField, setSortField] = useState(null);
  const [sortOrder, setSortOrder] = useState("asc");

  const sortedData = [...data].sort((a, b) => {
    if (!sortField) return 0;
    return sortOrder === "asc" ? a[sortField] - b[sortField] : b[sortField] - a[sortField];
  });

  const handleSort = (field) => {
    setSortOrder(sortField === field && sortOrder === "asc" ? "desc" : "asc");
    setSortField(field);
  };

  return (
    <table border="1">
      <thead>
        <tr>
          <th onClick={() => handleSort("name")}>Name</th>
          <th onClick={() => handleSort("age")}>Age</th>
        </tr>
      </thead>
      <tbody>
        {sortedData.map((row) => (
          <tr key={row.id}>
            <td>{row.name}</td>
            <td>{row.age}</td>
          </tr>
        ))}
      </tbody>
    </table>
  );
}
```
✅ **Concepts Used:** `useState`, sorting with `sort()`

---

## **2️⃣ Drag and Drop List (Using `react-beautiful-dnd`)**
```jsx
import { useState } from "react";
import { DragDropContext, Droppable, Draggable } from "react-beautiful-dnd";

const initialItems = ["Item 1", "Item 2", "Item 3", "Item 4"];

export default function DragDropList() {
  const [items, setItems] = useState(initialItems);

  const handleDragEnd = (result) => {
    if (!result.destination) return;
    const newItems = [...items];
    const [movedItem] = newItems.splice(result.source.index, 1);
    newItems.splice(result.destination.index, 0, movedItem);
    setItems(newItems);
  };

  return (
    <DragDropContext onDragEnd={handleDragEnd}>
      <Droppable droppableId="list">
        {(provided) => (
          <ul {...provided.droppableProps} ref={provided.innerRef}>
            {items.map((item, index) => (
              <Draggable key={item} draggableId={item} index={index}>
                {(provided) => (
                  <li ref={provided.innerRef} {...provided.draggableProps} {...provided.dragHandleProps}>
                    {item}
                  </li>
                )}
              </Draggable>
            ))}
            {provided.placeholder}
          </ul>
        )}
      </Droppable>
    </DragDropContext>
  );
}
```
✅ **Concepts Used:** `react-beautiful-dnd`, `useState`

---

## **3️⃣ Accordion Component (Expand/Collapse Sections)**
```jsx
import { useState } from "react";

const sections = [
  { id: 1, title: "Section 1", content: "Content for section 1" },
  { id: 2, title: "Section 2", content: "Content for section 2" },
];

export default function Accordion() {
  const [openSection, setOpenSection] = useState(null);

  return (
    <div>
      {sections.map((section) => (
        <div key={section.id}>
          <h3 onClick={() => setOpenSection(openSection === section.id ? null : section.id)}>
            {section.title}
          </h3>
          {openSection === section.id && <p>{section.content}</p>}
        </div>
      ))}
    </div>
  );
}
```
✅ **Concepts Used:** `useState`, conditional rendering

---

## **4️⃣ Multi-Step Form**
```jsx
import { useState } from "react";

export default function MultiStepForm() {
  const [step, setStep] = useState(1);
  const [formData, setFormData] = useState({ name: "", email: "", password: "" });

  const nextStep = () => setStep((prev) => prev + 1);
  const prevStep = () => setStep((prev) => prev - 1);

  return (
    <div>
      {step === 1 && (
        <div>
          <h2>Step 1: Enter Name</h2>
          <input type="text" placeholder="Name" onChange={(e) => setFormData({ ...formData, name: e.target.value })} />
          <button onClick={nextStep}>Next</button>
        </div>
      )}
      {step === 2 && (
        <div>
          <h2>Step 2: Enter Email</h2>
          <input type="email" placeholder="Email" onChange={(e) => setFormData({ ...formData, email: e.target.value })} />
          <button onClick={prevStep}>Back</button>
          <button onClick={nextStep}>Next</button>
        </div>
      )}
      {step === 3 && (
        <div>
          <h2>Step 3: Enter Password</h2>
          <input type="password" placeholder="Password" onChange={(e) => setFormData({ ...formData, password: e.target.value })} />
          <button onClick={prevStep}>Back</button>
          <button onClick={() => alert("Form Submitted")}>Submit</button>
        </div>
      )}
    </div>
  );
}
```
✅ **Concepts Used:** `useState`, multi-step UI navigation

---

## **5️⃣ Image Carousel (Auto-scroll & Manual Buttons)**
```jsx
import { useState, useEffect } from "react";

const images = [
  "https://via.placeholder.com/400x200/FF5733",
  "https://via.placeholder.com/400x200/33FF57",
  "https://via.placeholder.com/400x200/3357FF"
];

export default function ImageCarousel() {
  const [index, setIndex] = useState(0);

  useEffect(() => {
    const interval = setInterval(() => setIndex((prev) => (prev + 1) % images.length), 3000);
    return () => clearInterval(interval);
  }, []);

  return (
    <div>
      <img src={images[index]} alt="carousel" width="400" height="200" />
      <div>
        <button onClick={() => setIndex((index - 1 + images.length) % images.length)}>Prev</button>
        <button onClick={() => setIndex((index + 1) % images.length)}>Next</button>
      </div>
    </div>
  );
}
```
✅ **Concepts Used:** `useState`, `useEffect`, auto-scroll with `setInterval`

---

### **🔥 Summary**
| Task | Key Concept |
|------|------------|
| Dynamic Table | Sorting (`sort()`), `useState` |
| Drag & Drop | `react-beautiful-dnd`, `useState` |
| Accordion | Toggle sections, `useState` |
| Multi-Step Form | Form navigation, `useState` |
| Image Carousel | `useEffect`, `setInterval()` |

---

Here are solutions for your **Context API, useReducer, Lazy Loading, Memoization, and Custom Hook** tasks:  

---

## **1️⃣ Global State Management with Context API (Authentication Example)**
```jsx
import { createContext, useContext, useState } from "react";

// Create Auth Context
const AuthContext = createContext();

// Auth Provider Component
export function AuthProvider({ children }) {
  const [isAuthenticated, setIsAuthenticated] = useState(false);

  const login = () => setIsAuthenticated(true);
  const logout = () => setIsAuthenticated(false);

  return (
    <AuthContext.Provider value={{ isAuthenticated, login, logout }}>
      {children}
    </AuthContext.Provider>
  );
}

// Custom Hook for Accessing Auth Context
export function useAuth() {
  return useContext(AuthContext);
}

// Example Usage
export function Navbar() {
  const { isAuthenticated, login, logout } = useAuth();

  return (
    <nav>
      <h3>{isAuthenticated ? "Logged In" : "Logged Out"}</h3>
      <button onClick={isAuthenticated ? logout : login}>
        {isAuthenticated ? "Logout" : "Login"}
      </button>
    </nav>
  );
}

// App Component
export default function App() {
  return (
    <AuthProvider>
      <Navbar />
    </AuthProvider>
  );
}
```
✅ **Concepts Used:** `createContext`, `useContext`, `useState`  

---

## **2️⃣ useReducer Instead of useState (Counter Example)**
```jsx
import { useReducer } from "react";

// Reducer Function
function counterReducer(state, action) {
  switch (action.type) {
    case "increment":
      return { count: state.count + 1 };
    case "decrement":
      return { count: state.count - 1 };
    case "reset":
      return { count: 0 };
    default:
      return state;
  }
}

export default function Counter() {
  const [state, dispatch] = useReducer(counterReducer, { count: 0 });

  return (
    <div>
      <h2>Count: {state.count}</h2>
      <button onClick={() => dispatch({ type: "increment" })}>+</button>
      <button onClick={() => dispatch({ type: "decrement" })}>-</button>
      <button onClick={() => dispatch({ type: "reset" })}>Reset</button>
    </div>
  );
}
```
✅ **Concepts Used:** `useReducer`, state management  

---

## **3️⃣ Lazy Loading Components (React.lazy & Suspense)**
```jsx
import { lazy, Suspense } from "react";

const HeavyComponent = lazy(() => import("./HeavyComponent"));

export default function App() {
  return (
    <div>
      <h2>Lazy Loading Example</h2>
      <Suspense fallback={<h3>Loading...</h3>}>
        <HeavyComponent />
      </Suspense>
    </div>
  );
}
```
✅ **Concepts Used:** `React.lazy()`, `Suspense`, performance optimization  

---

## **4️⃣ Memoization with `useMemo` & `useCallback`**
```jsx
import { useState, useMemo, useCallback } from "react";

// Expensive Calculation
function slowFunction(num) {
  console.log("Computing...");
  for (let i = 0; i < 1e9; i++) {} // Simulating heavy computation
  return num * 2;
}

export default function MemoExample() {
  const [count, setCount] = useState(0);
  const [number, setNumber] = useState(2);

  const doubledNumber = useMemo(() => slowFunction(number), [number]);

  const increment = useCallback(() => setCount(count + 1), [count]);

  return (
    <div>
      <h2>Count: {count}</h2>
      <button onClick={increment}>Increment</button>
      <h2>Number: {number}</h2>
      <button onClick={() => setNumber(number + 1)}>Increase Number</button>
      <h3>Result: {doubledNumber}</h3>
    </div>
  );
}
```
✅ **Concepts Used:** `useMemo` (memoize expensive calculation), `useCallback` (memoize function)  

---

## **5️⃣ Custom Hook for API Fetching (`useFetch`)**
```jsx
import { useState, useEffect } from "react";

// Custom Hook
export function useFetch(url) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    setLoading(true);
    fetch(url)
      .then((res) => res.json())
      .then((data) => {
        setData(data);
        setLoading(false);
      })
      .catch((err) => {
        setError(err);
        setLoading(false);
      });
  }, [url]);

  return { data, loading, error };
}

// Example Usage
export default function Users() {
  const { data, loading, error } = useFetch("https://jsonplaceholder.typicode.com/users");

  if (loading) return <h3>Loading...</h3>;
  if (error) return <h3>Error: {error.message}</h3>;

  return (
    <ul>
      {data.map((user) => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
}
```
✅ **Concepts Used:** `Custom Hook`, `fetch()`, `useEffect`, `useState`  

---

### **🔥 Summary Table**
| Task | Key Concept |
|------|------------|
| Context API | Global State (`createContext`, `useContext`) |
| useReducer | Alternative to `useState`, better for complex state |
| Lazy Loading | Optimize performance (`React.lazy()`, `Suspense`) |
| Memoization | Optimize re-renders (`useMemo`, `useCallback`) |
| Custom Hook | Encapsulate API fetching logic (`useFetch()`) |



Here are the solutions for your **Protected Routes, SSR vs CSR in Next.js, Pagination, WebSockets, and PWA Setup** tasks:

---

## **1️⃣ Protected Routes in React (React Router + Context API)**  
Restrict certain routes based on authentication.

### **🔹 Steps:**  
1. Create an `AuthContext` for authentication state.  
2. Create a `ProtectedRoute` component.  
3. Use `ProtectedRoute` in `React Router`.  

```jsx
import React, { createContext, useContext, useState } from "react";
import { BrowserRouter as Router, Routes, Route, Navigate } from "react-router-dom";

// Create Authentication Context
const AuthContext = createContext();

function AuthProvider({ children }) {
  const [isAuthenticated, setIsAuthenticated] = useState(false);
  
  const login = () => setIsAuthenticated(true);
  const logout = () => setIsAuthenticated(false);
  
  return (
    <AuthContext.Provider value={{ isAuthenticated, login, logout }}>
      {children}
    </AuthContext.Provider>
  );
}

// Custom Hook to Access Auth Context
function useAuth() {
  return useContext(AuthContext);
}

// Protected Route Component
function ProtectedRoute({ children }) {
  const { isAuthenticated } = useAuth();
  return isAuthenticated ? children : <Navigate to="/login" />;
}

// Sample Pages
function Home() {
  return <h2>Home Page (Public)</h2>;
}

function Dashboard() {
  return <h2>Dashboard (Protected)</h2>;
}

function Login() {
  const { login } = useAuth();
  return <button onClick={login}>Login</button>;
}

// App with Routing
function App() {
  return (
    <AuthProvider>
      <Router>
        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/login" element={<Login />} />
          <Route path="/dashboard" element={<ProtectedRoute><Dashboard /></ProtectedRoute>} />
        </Routes>
      </Router>
    </AuthProvider>
  );
}

export default App;
```
✅ **Concepts Used:** `React Router`, `useContext`, `useState`  

---

## **2️⃣ SSR vs CSR in Next.js**  
### **Client-Side Rendering (CSR) – Fetching data in useEffect**
```jsx
import { useState, useEffect } from "react";

export default function CSRPage() {
  const [data, setData] = useState([]);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/posts")
      .then((res) => res.json())
      .then((data) => setData(data));
  }, []);

  return (
    <div>
      <h2>Client-Side Rendering (CSR)</h2>
      {data.slice(0, 5).map((post) => (
        <p key={post.id}>{post.title}</p>
      ))}
    </div>
  );
}
```
✅ **Concepts Used:** `useEffect`, `useState`, `fetch()`  

### **Server-Side Rendering (SSR) – Fetching data with getServerSideProps**
```jsx
export async function getServerSideProps() {
  const res = await fetch("https://jsonplaceholder.typicode.com/posts");
  const data = await res.json();

  return {
    props: { data },
  };
}

export default function SSRPage({ data }) {
  return (
    <div>
      <h2>Server-Side Rendering (SSR)</h2>
      {data.slice(0, 5).map((post) => (
        <p key={post.id}>{post.title}</p>
      ))}
    </div>
  );
}
```
✅ **Concepts Used:** `getServerSideProps()`, `fetch()`

---

## **3️⃣ Pagination in React**
Fetching paginated data from an API.

```jsx
import { useState, useEffect } from "react";

export default function PaginatedList() {
  const [data, setData] = useState([]);
  const [page, setPage] = useState(1);

  useEffect(() => {
    fetch(`https://jsonplaceholder.typicode.com/posts?_page=${page}&_limit=5`)
      .then((res) => res.json())
      .then((data) => setData(data));
  }, [page]);

  return (
    <div>
      <h2>Pagination</h2>
      {data.map((post) => (
        <p key={post.id}>{post.title}</p>
      ))}
      <button disabled={page === 1} onClick={() => setPage(page - 1)}>Previous</button>
      <button onClick={() => setPage(page + 1)}>Next</button>
    </div>
  );
}
```
✅ **Concepts Used:** `useState`, `useEffect`, API fetching  

---

## **4️⃣ WebSockets with React (Chat App using `socket.io`)**
1. Install dependencies:  
   ```
   npm install socket.io-client
   ```

2. **Frontend (React)**
```jsx
import { useState, useEffect } from "react";
import io from "socket.io-client";

const socket = io("http://localhost:5000"); // Backend URL

export default function Chat() {
  const [messages, setMessages] = useState([]);
  const [input, setInput] = useState("");

  useEffect(() => {
    socket.on("message", (msg) => setMessages((prev) => [...prev, msg]));
  }, []);

  const sendMessage = () => {
    socket.emit("message", input);
    setInput("");
  };

  return (
    <div>
      <h2>Chat App</h2>
      <div>
        {messages.map((msg, i) => (
          <p key={i}>{msg}</p>
        ))}
      </div>
      <input value={input} onChange={(e) => setInput(e.target.value)} />
      <button onClick={sendMessage}>Send</button>
    </div>
  );
}
```

3. **Backend (Node.js + Express + Socket.io)**
```javascript
const express = require("express");
const http = require("http");
const { Server } = require("socket.io");

const app = express();
const server = http.createServer(app);
const io = new Server(server, { cors: { origin: "*" } });

io.on("connection", (socket) => {
  console.log("New client connected");

  socket.on("message", (msg) => {
    io.emit("message", msg);
  });

  socket.on("disconnect", () => {
    console.log("Client disconnected");
  });
});

server.listen(5000, () => console.log("Server running on port 5000"));
```
✅ **Concepts Used:** `socket.io-client`, `useEffect`, `useState`

---

## **5️⃣ Progressive Web App (PWA) Setup**
### **Steps to Convert a React App into a PWA**
1. Install `react-pwa`
   ```sh
   npm install workbox-cli --save-dev
   ```

2. **Enable PWA in `public/manifest.json`**
```json
{
  "short_name": "PWA App",
  "name": "My Progressive Web App",
  "icons": [
    {
      "src": "logo192.png",
      "sizes": "192x192",
      "type": "image/png"
    },
    {
      "src": "logo512.png",
      "sizes": "512x512",
      "type": "image/png"
    }
  ],
  "start_url": ".",
  "display": "standalone",
  "theme_color": "#000000",
  "background_color": "#ffffff"
}
```

3. **Register Service Worker (`src/serviceWorker.js`)**
```javascript
export function registerServiceWorker() {
  if ("serviceWorker" in navigator) {
    navigator.serviceWorker.register("/service-worker.js")
      .then(() => console.log("Service Worker Registered"));
  }
}
```

4. **Enable Service Worker in `index.js`**
```javascript
import { registerServiceWorker } from "./serviceWorker";
registerServiceWorker();
```
✅ **Concepts Used:** `manifest.json`, `service workers`, `offline caching`

---

### **🔥 Summary**
| Task | Key Concept |
|------|------------|
| Protected Routes | `React Router`, `useContext` |
| SSR vs CSR | `getServerSideProps()`, `useEffect()` |
| Pagination | API Fetching, `useState`, `useEffect` |
| WebSockets | Real-time chat, `socket.io-client` |
| PWA Setup | `Service Workers`, `Manifest.json` |

Would you like any modifications or explanations? 🚀


Here's a simple **counter program** in React using functional components and hooks (`useState`):  

---

### Features:  
✅ Increase Count  
✅ Decrease Count  
✅ Reset Count  

---

### Code:
```jsx
import { useState } from "react";

export default function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div className="flex flex-col items-center justify-center min-h-screen bg-gray-100">
      <h1 className="text-2xl font-bold mb-4">Counter App</h1>
      <div className="text-4xl font-bold mb-4">{count}</div>
      <div className="space-x-2">
        <button
          onClick={() => setCount(count + 1)}
          className="px-4 py-2 bg-green-500 text-white rounded-lg"
        >
          Increase
        </button>
        <button
          onClick={() => setCount(count - 1)}
          className="px-4 py-2 bg-red-500 text-white rounded-lg"
        >
          Decrease
        </button>
        <button
          onClick={() => setCount(0)}
          className="px-4 py-2 bg-gray-500 text-white rounded-lg"
        >
          Reset
        </button>
      </div>
    </div>
  );
}
```

---

### Steps to Run:
1. Install React (`npx create-react-app my-app` if not set up).  
2. Replace the `App.js` content with the above code.  
3. Run `npm start`.  

This uses **Tailwind CSS** for styling. If you haven’t installed Tailwind, you can replace the classes with normal CSS. Let me know if you need a **Next.js** version or additional features! 🚀


1. [Counter](#head1)
2. [Random Number Generator](#head2)
3. [Calculator](#head3)
4. [Forms](#head4)


### <a name="head1">1. Counter</a>
```````````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <h1>Counter:<span id="counter-value">0</span></h1>
    <button id="incrementBtn">Increment</button>
    <button id="decrementBtn">Decrement</button>
    <button id="resetBtn">reset</button>

    <script src="index.js"></script>
</body>
</html>
``````````````

Algorithm

`````````````````css
1. Initialize CounterValue to 0, store dom element in counterDisplay
2. Define Functions for Counter Operations, increment(), decrement reset and call update in each functions
3. Function to Update Counter Display, set textContent of counterDisplay to current counterValue
4. Add Event Listeners to Buttons, click and functions

``````````````````


``````````````js
let counterValue = 0;
const counterDisplay = document.getElementById('counter-value');

function increment() {
    counterValue++;
    updateCounterDisplay();
}
function decrement() {
    counterValue--;
    updateCounterDisplay();
}
function reset() {
    counterValue = 0;
    updateCounterDisplay();
}
function updateCounterDisplay() {
   counterDisplay.textContent = counterValue;
}
document.getElementById('incrementBtn').addEventListener('click', increment);
document.getElementById('decrementBtn').addEventListener('click', decrement);
document.getElementById('resetBtn').addEventListener('click', reset);

````````````````

### <a name="head2">2. Random Number Generator</a>
```````````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <button id="myButton">Generate</button>
    <p><span id="label1">0</span></p>
    <p><span id="label2">0</span></p>
    <p><span id="label3">0</span></p>

    <script src="index.js"></script>
</body>
</html>
``````````````

Algorithm
``````````````````css
Algorithm Steps for Random Number Generator
1. Select DOM Elements store d store it in the variable myButton.
2. Select the label elements with IDs label1, label2, and label3 and store them in an array called labels.
3. Define Range for Random Number [0, 6]
4. Function to Generate a Random Number return Math.floor(Math.random() * max) + min;
5. Function to Update Labels with Random Numbers
6. Add Event Listener to the Button

````````````````````

``````````````js
const myButton = document.getElementById('myButton');
const labels = [
    document.getElementById('label1'),
    document.getElementById('label2'),
    document.getElementById('label3')
];

const min =0;
const max =6;

function generateRandomNumber(){
    return Math.floor(Math.random() * max) + min;
}

function updateLabel(){
    labels.forEach((label) => {
        const randomNumber = generateRandomNumber();    
        label.textContent = randomNumber;
    });
}

myButton.addEventListener('click', updateLabel);
````````````````

### <a name="head3">3. Calculator</a>
```````````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculator</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="calculator">
        <!-- Display for the calculator -->
        <input type="text" id="display" disabled>

        <!-- Calculator buttons -->
        <div class="buttons">
            <button>C</button>
            <button>/</button>
            <button>*</button>
            <button>DEL</button>
            
            <button>7</button>
            <button>8</button>
            <button>9</button>
            <button>-</button>
             
            <button>4</button>
            <button>5</button>
            <button>6</button>
            <button>+</button>
            
            <button>1</button>
            <button>2</button>
            <button>3</button>
            <button>=</button>
            
            <button class="zero">0</button>
            <button>.</button>
        </div>
    </div>

    <!-- Linking the JavaScript file -->
    <script src="index.js"></script>
</body>
</html>

``````````````


``````````````js
// Select the display element
const display = document.getElementById('display');

// Select all buttons
const buttons = document.querySelectorAll('.buttons button');

// Attach event listener to each button
buttons.forEach(button => {
    button.addEventListener('click', () => {
        const value = button.textContent;

        if (value === 'C') {
            clearDisplay();
        } else if (value === 'DEL') {
            deleteLast();
        } else if (value === '=') {
            calculate();
        } else {
            appendValue(value);
        }
    });
});

// Function to append values to the display
function appendValue(value) {
    display.value += value;
}

// Function to clear the display
function clearDisplay() {
    display.value = '';
}

// Function to delete the last character
function deleteLast() {
    display.value = display.value.slice(0, -1);
}

// Function to calculate the result
function calculate() {
    try {
        display.value = eval(display.value);
    } catch (error) {
        display.value = 'Error';
    }

}

````````````````

````````````````css
body {
    font-family: Arial, sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background-color: #f0f0f0;
    margin: 0;
}

.calculator {
    background-color: #fff;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
}

#display {
    width: 100%;
    height: 50px;
    font-size: 24px;
    text-align: right;
    border: none;
    margin-bottom: 10px;
    padding-right: 10px;
    border-radius: 5px;
    background-color: #f9f9f9;
}

.buttons {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
}

button {
    height: 50px;
    font-size: 18px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    background-color: #e0e0e0;
}

button:hover {
    background-color: #d6d6d6;
}

button:active {
    background-color: #cccccc;
}

.zero {
    grid-column: span 2;
}

`````````````````
### <a name="head4">4. Forms</a>
``````````````````````````css
Algorithm of Forms
Html
1. Forms id, label for= elementName,  [input types = email, password, tel, submit], required
2. one more div to display error msg, and css -color, font-size

 Js
1. Add Event Listener for Form Submission, addEventListener(), event.preventDefault()
2. Clear Previous Errors, textContent- clearing error
3. Validate Each Field- email(@), password(10-14), confirm password(value)
4. PhoneNumberValidation, Check Validation Result
5. Check Validation Result- isValid, this.submit
````````````````````````````````````````````````````````````````
``````````````````````js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Form Validation</title>
    <style>
        .error {
            color: red;
            font-size: 14px;
        }
    </style>
</head>
<body>
    <h2>Form Validation</h2>
    <form id="myForm">
        <label for="email">Email:</label>
        <input type="email" id="email" name="email" required>
        <div id="emailError" class="error"></div><br>

        <label for="password">Password (10-14 characters):</label>
        <input type="password" id="password" name="password" required>
        <div id="passwordError" class="error"></div><br>

        <label for="confirmPassword">Confirm Password:</label>
        <input type="password" id="confirmPassword" name="confirmPassword" required>
        <div id="confirmPasswordError" class="error"></div><br>

        <label for="phone">Phone Number:</label>
        <input type="tel" id="phone" name="phone" maxlength="10" required>
        <div id="phoneError" class="error"></div><br>
        <label for="password">Email:</label>
        

        <button type="submit">Submit</button>
    </form>

    <script>
        document.getElementById("myForm").addEventListener("submit", function(event) {
            event.preventDefault(); // Prevent form submission

            // Clear previous errors
            document.getElementById("emailError").textContent = "";
            document.getElementById("passwordError").textContent = "";
            document.getElementById("confirmPasswordError").textContent = "";
            document.getElementById("phoneError").textContent = "";

            let isValid = true;

            // Email validation
            const email = document.getElementById("email").value;
            if (!email.includes("@")) {
                document.getElementById("emailError").textContent = "Please enter a valid email address.";
                isValid = false;
            }

            // Password validation
            const password = document.getElementById("password").value;
            if (password.length < 10 || password.length > 14) {
                document.getElementById("passwordError").textContent = "Password must be between 10 and 14 characters.";
                isValid = false;
            }

            // Confirm password validation
            const confirmPassword = document.getElementById("confirmPassword").value;
            if (password !== confirmPassword) {
                document.getElementById("confirmPasswordError").textContent = "Passwords do not match.";
                isValid = false;
            }

            // Phone number validation
            const phone = document.getElementById("phone").value;
            const phonePattern = /^[6789]\d{9}$/;
            if (!phonePattern.test(phone)) {
                document.getElementById("phoneError").textContent = "Phone number must start with 6, 7, 8, or 9 and be 10 digits long.";
                isValid = false;
            }

            // Submit form if valid
            if (isValid) {
                alert("Form submitted successfully!");
                // You can proceed with the form submission or further processing here.
                this.submit();
            }
        });
    </script>
</body>
</html>

```````````````````````````
`````````````````````````````````````jsx
import { useState } from "react";

const SignUpForm = () => {
  const [formData, setFormData] = useState({
    firstName: "",
    lastName: "",
    username: "",
    email: "",
    password: "",
    phone: "",
    dob: ""
  });

  const [errors, setErrors] = useState({});

  const validate = () => {
    let newErrors = {};
    const nameRegex = /^[a-zA-Z]{1,30}$/;
    const userRegex = /^[a-zA-Z0-9_]{3,15}$/;
    const emailRegex = /^([a-zA-Z0-9._%+-]+)@([a-zA-Z0-9.-]+)\.([a-zA-Z]{2,})$/;
    const passRegex = /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%?&])[A-Za-z\d@$!%?&]{8,}$/;
    const phoneRegex = /^[7-9][0-9]{9}$/;
    
    if (!nameRegex.test(formData.firstName)) newErrors.firstName = "First name must be 1-30 letters.";
    if (!nameRegex.test(formData.lastName)) newErrors.lastName = "Last name must be 1-30 letters.";
    if (!userRegex.test(formData.username)) newErrors.username = "Username must be 3-15 chars (letters, numbers, underscores).";
    if (!emailRegex.test(formData.email)) newErrors.email = "Invalid email address.";
    if (!passRegex.test(formData.password)) newErrors.password = "Password must have 8+ chars, 1 uppercase, 1 number, 1 special char.";
    if (!phoneRegex.test(formData.phone)) newErrors.phone = "Phone must be 10 digits, starting with 7-9.";
    
    const today = new Date();
    const birthDate = new Date(formData.dob);
    const age = today.getFullYear() - birthDate.getFullYear();
    if (age < 18) newErrors.dob = "You must be at least 18 years old.";
    
    setErrors(newErrors);
    return Object.keys(newErrors).length === 0;
  };

  const handleChange = (e) => {
    setFormData({ ...formData, [e.target.name]: e.target.value });
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    if (validate()) {
      alert("Form submitted successfully!");
    }
  };

  return (
    <div className="flex justify-center items-center min-h-screen bg-gray-100">
      <div className="bg-white p-6 rounded-lg shadow-lg w-96">
        <h2 className="text-center text-2xl font-bold text-gray-700">Sign Up</h2>
        <form onSubmit={handleSubmit}>
          {Object.entries(formData).map(([key, value]) => (
            <div key={key} className="mb-3">
              <input
                type={key === "password" ? "password" : key === "dob" ? "date" : key === "email" ? "email" : "text"}
                name={key}
                value={value}
                onChange={handleChange}
                placeholder={key.replace(/([A-Z])/g, " $1").trim()}
                className="w-full p-2 border border-gray-300 rounded"
                required
              />
              {errors[key] && <p className="text-red-500 text-sm">{errors[key]}</p>}
            </div>
          ))}
          <button type="submit" className="w-full p-2 bg-green-500 text-white rounded hover:bg-green-600">
            Submit
          </button>
        </form>
      </div>
    </div>
  );
};

export default SignUpForm;
```````````````````````````````````````````





