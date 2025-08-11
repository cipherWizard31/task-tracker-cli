# **Task Tracker CLI - Documentation**  
A simple command-line task manager built with **Node.js** that helps you track your tasks (Todo, In Progress, Done) and stores them in a **JSON file**.  

---

## **📥 Installation**  
1. Ensure you have **Node.js** installed (v14+).  
2. Clone/download the project.  
3. Run the CLI directly using `node task-cli.js [command]`.  

*(Optional: Make it globally executable by adding a shebang `#!/usr/bin/env node` and running `chmod +x task-cli.js`.)*  

---

## **🛠️ Commands & Usage**  

| Command | Usage | Description |
|---------|-------|-------------|
| **Add Task** | `task-cli add "Description"` | Adds a new task (default: `status: "todo"`). |
| **Update Task** | `task-cli update [id] "New Description"` | Updates a task’s description. |
| **Delete Task** | `task-cli delete [id]` | Deletes a task by ID. |
| **Mark as In Progress** | `task-cli mark-in-progress [id]` | Changes status to `in-progress`. |
| **Mark as Done** | `task-cli mark-done [id]` | Changes status to `done`. |
| **List All Tasks** | `task-cli list` | Shows all tasks. |
| **List by Status** | `task-cli list [todo/in-progress/done]` | Filters tasks by status. |

---

## **📂 Data Structure (JSON Storage)**  
Tasks are stored in `tasks.json` with the following schema:  
```json
[
  {
    "id": 1,
    "description": "Buy groceries",
    "status": "todo",
    "createdAt": "2024-03-15T10:00:00Z",
    "updatedAt": "2024-03-15T10:00:00Z"
  }
]
```
- **`id`**: Auto-incremented unique identifier.  
- **`status`**: `todo` (default), `in-progress`, or `done`.  
- **Timestamps**: Automatically generated in ISO format.  

*(File is created automatically if missing.)*  

---

## **⚙️ Technical Implementation**  
### **1. Core Functions**  
- **`addTask(description)`**: Appends a new task to `tasks.json`.  
- **`updateTask(id, newDescription)`**: Modifies a task’s description.  
- **`deleteTask(id)`**: Removes a task by ID.  
- **`markStatus(id, status)`**: Updates a task’s status (`todo/in-progress/done`).  
- **`listTasks(filterStatus)`**: Displays tasks (optionally filtered).  

### **2. Error Handling**  
- Validates user inputs (e.g., `id` must exist).  
- Handles file read/write errors gracefully.  

### **3. File System Operations**  
Uses Node.js `fs` module:  
```javascript
const fs = require('fs');
const tasks = JSON.parse(fs.readFileSync('tasks.json'));
fs.writeFileSync('tasks.json', JSON.stringify(tasks, null, 2));
```

---

## **🚀 Example Workflow**  
```bash
# Add tasks
node task-cli.js add "Write docs"
node task-cli.js add "Debug code"

# Update & mark status
node task-cli.js update 1 "Write project documentation"
node task-cli.js mark-in-progress 1

# List tasks
node task-cli.js list
node task-cli.js list in-progress

# Delete a task
node task-cli.js delete 2
```

---

## **🔧 Edge Cases & Validation**  
- Rejects empty descriptions.  
- Ensures `id` exists before updating/deleting.  
- Auto-creates `tasks.json` if missing.  

---

## **📜 License**  
MIT License - Free for personal and commercial use.  

---

### **🎯 Next Steps**  
- Add **due dates** and **priority levels**.  
- Support **search/filtering** by keyword.  
- Implement **colorized output** for better readability.  

---

**Enjoy tracking your tasks!** 🚀  

*(For contributors: PRs welcome!)*