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
