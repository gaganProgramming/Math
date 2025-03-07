# For the given api fetch firstName of the users 
  ``````````````````````````````````````````````````````jsx
import React, { useState, useEffect } from "react";

const App = () => {
  const [user, setUser] = useState([]);
  const apiLink = "https://dummyjson.com/users";

  useEffect(() => {
    async function fetchAPI() {
      fetch(apiLink)
        .then((res) => res.json())
        .then((res) => setUser(res.users))
        .catch((err) => console.log(err));
    }
    fetchAPI();
  }, []);

  return (
    <div className="App">
      <h1>Hello Code Sandbox</h1>
      {user?.map((data, i) => {
        return <p key={i}>{data.firstName}</p>;
      })}
    </div>
  );
};
export default App;


  ```````````````````````````````````````````````````````


Here's the **easiest To-Do List** using **pure React (without localStorage, separate components, or extra styling)**. You can memorize this in **under 10 minutes** and build it in an interview quickly! 🚀  
# Todo- list

## **🔹 Full Code (React + useState)**
```jsx
import { useState } from "react";

export default function TodoApp() {
  const [tasks, setTasks] = useState([]);
  const [input, setInput] = useState("");

  const addTask = () => {
    if (!input.trim()) return;
    setTasks([...tasks, { id: Date.now(), text: input }]);
    setInput("");
  };

  const deleteTask = (id) => {
    setTasks(tasks.filter((task) => task.id !== id));
  };

  return (
    <div>
      <h2>To-Do List</h2>
      <input value={input} onChange={(e) => setInput(e.target.value)} placeholder="Add a task" />
      <button onClick={addTask}>Add</button>
      <ul>
        {tasks.map((task) => (
          <li key={task.id}>
            {task.text} <button onClick={() => deleteTask(task.id)}>❌</button>
          </li>
        ))}
      </ul>
    </div>
  );
}
```

---

## **⏳ How to Memorize in 10 Minutes**
### **1️⃣ Break It Down into 3 Parts**  
- **State Management (`useState`)** → Stores tasks  
- **Add & Delete Tasks (`addTask`, `deleteTask`)** → Modify tasks  
- **UI (`input`, `ul`, `li`)** → Displays tasks  

### **2️⃣ Memory Tricks**  
- **Notebook analogy 📓** → `useState([])` holds the tasks  
- **Write task 📝** → `setTasks([...tasks, { id: Date.now(), text: input }])`  
- **Erase task 🧽** → `filter((task) => task.id !== id)`  

### **3️⃣ Practice Plan**
⏳ **5 mins:** Read & repeat code out loud  
⏳ **3 mins:** Close this tab and write from memory  
⏳ **2 mins:** Test in CodeSandbox or VS Code  

💡 **Done! You can now build this in an interview under 10 minutes.** 🚀  
### **React To-Do List Code & Memorization Plan (4-5 Hours)**  

This plan ensures you **memorize the logic quickly** while coding efficiently.  

---

## **🕒 Step-by-Step Learning Plan**  

| **Step** | **Task** | **Time** |
|----------|---------|---------|
| 1️⃣ **Understand the Features** | Read and analyze the core features. | **15 mins** |
| 2️⃣ **Type Out the Code Once** | Code the React To-Do List **without copy-pasting**. | **1 hour** |
| 3️⃣ **Break the Code Into Small Parts** | Study `useState`, `localStorage`, `event handling`, and component structure. | **30 mins** |
| 4️⃣ **Write Code on Paper (From Memory)** | Recall and write key parts manually. | **30 mins** |
| 5️⃣ **Build Again From Memory** | Code the entire project without looking at the original. | **1 hour** |
| 6️⃣ **Explain to Yourself (Mock Interview)** | Speak out loud and explain logic like in an interview. | **30 mins** |
| 7️⃣ **Daily 10-Minute Recap** | Before an interview, recall the logic & practice. | **10 mins/day** |

---

## **📌 React To-Do List Code (Memorization-Friendly)**  

### **1️⃣ Setup (Create React App & Install Dependencies)**
```sh
npx create-react-app todo-app
cd todo-app
npm start
```

---

### **2️⃣ `App.js` (Main Logic)**
```jsx
import React, { useState, useEffect } from "react";

const App = () => {
  const [tasks, setTasks] = useState([]);

  // Load tasks from localStorage on first render
  useEffect(() => {
    const savedTasks = JSON.parse(localStorage.getItem("tasks")) || [];
    setTasks(savedTasks);
  }, []);

  // Save tasks to localStorage whenever tasks change
  useEffect(() => {
    localStorage.setItem("tasks", JSON.stringify(tasks));
  }, [tasks]);

  const addTask = (task) => {
    if (task.trim() === "") return;
    setTasks([...tasks, { id: Date.now(), text: task, completed: false }]);
  };

  const toggleComplete = (id) => {
    setTasks(
      tasks.map((task) =>
        task.id === id ? { ...task, completed: !task.completed } : task
      )
    );
  };

  const deleteTask = (id) => {
    setTasks(tasks.filter((task) => task.id !== id));
  };

  return (
    <div style={{ textAlign: "center", marginTop: "50px" }}>
      <h2>To-Do List</h2>
      <TaskInput addTask={addTask} />
      <TaskList tasks={tasks} toggleComplete={toggleComplete} deleteTask={deleteTask} />
    </div>
  );
};

const TaskInput = ({ addTask }) => {
  const [input, setInput] = useState("");

  const handleSubmit = (e) => {
    e.preventDefault();
    addTask(input);
    setInput("");
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        type="text"
        value={input}
        onChange={(e) => setInput(e.target.value)}
        placeholder="Add a task..."
      />
      <button type="submit">Add</button>
    </form>
  );
};

const TaskList = ({ tasks, toggleComplete, deleteTask }) => (
  <ul>
    {tasks.map((task) => (
      <li key={task.id} style={{ textDecoration: task.completed ? "line-through" : "none" }}>
        {task.text}
        <button onClick={() => toggleComplete(task.id)}>✔</button>
        <button onClick={() => deleteTask(task.id)}>❌</button>
      </li>
    ))}
  </ul>
);

export default App;
```

---

## **🔹 How to Memorize This Code Quickly**
### **1️⃣ Break It Down Into Small Parts**
- **State Management (`useState`)**: Holds the tasks.  
- **Local Storage (`useEffect`)**: Saves and loads tasks.  
- **Event Handling (`onSubmit`, `onClick`)**: Handles adding, deleting, and completing tasks.  

### **2️⃣ Core Functions to Memorize**
- **Adding a task** → `addTask(task)`
- **Marking complete** → `toggleComplete(id)`
- **Deleting a task** → `deleteTask(id)`

### **3️⃣ Recall the Flow Like a Story**
1. **User enters a task** → `addTask()`
2. **Tasks appear from `useState`** and are saved in `localStorage`
3. **User can mark as complete (`toggleComplete`)**
4. **User can delete a task (`deleteTask`)**
5. **Changes are stored in `localStorage`**

---

## **🎯 Final Challenge (Testing Your Memory)**
After following the **4-5 hour** learning plan:  
✅ **Write the key functions (`addTask`, `toggleComplete`, `deleteTask`) on paper**  
✅ **Build the project again WITHOUT looking at the code**  
✅ **Explain the logic out loud as if in an interview**  

If you can **build and explain it in under 5 minutes**, you’re ready!  

Want a more advanced version with **drag-and-drop or a database (MongoDB)?**
