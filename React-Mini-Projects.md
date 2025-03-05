# Todos 
`````````````````````````````````````````````````jsx
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


```````````````````````````````````````````````````


Here's the **easiest To-Do List** using **pure React (without localStorage, separate components, or extra styling)**. You can memorize this in **under 10 minutes** and build it in an interview quickly! 🚀  

---

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

Would you like an **editable version on CodeSandbox?** 😊
