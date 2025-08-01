<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Simple To-Do List</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div class="todo-container">
    <h1>📝 My To-Do List</h1>
    <div class="input-section">
      <input type="text" id="taskInput" placeholder="Enter a new task...">
      <button onclick="addTask()">Add</button>
    </div>
    <ul id="taskList"></ul>
  </div>

  <script src="script.js"></script>
</body>
</html>

body {
  font-family: Arial, sans-serif;
  background: #f5f5f5;
  padding: 40px;
  display: flex;
  justify-content: center;
}

.todo-container {
  background: white;
  padding: 30px;
  border-radius: 8px;
  width: 100%;
  max-width: 400px;
  box-shadow: 0 0 10px rgba(0,0,0,0.1);
}

h1 {
  text-align: center;
  margin-bottom: 20px;
}

.input-section {
  display: flex;
  gap: 10px;
}

input {
  flex: 1;
  padding: 10px;
  font-size: 16px;
}

button {
  padding: 10px 15px;
  background-color: #28a745;
  border: none;
  color: white;
  cursor: pointer;
  font-weight: bold;
  border-radius: 4px;
}

button:hover {
  background-color: #218838;
}

ul {
  list-style-type: none;
  padding-left: 0;
  margin-top: 20px;
}

li {
  padding: 10px;
  background: #eee;
  margin-bottom: 10px;
  display: flex;
  justify-content: space-between;
  border-radius: 4px;
}

li.done {
  text-decoration: line-through;
  color: gray;
}

li button {
  background: #dc3545;
  border: none;
  color: white;
  padding: 5px 10px;
  cursor: pointer;
  border-radius: 3px;
}

li button:hover {
  background: #c82333;
}


function addTask() {
  const input = document.getElementById("taskInput");
  const taskText = input.value.trim();

  if (taskText === "") {
    alert("Please enter a task!");
    return;
  }

  const li = document.createElement("li");
  li.textContent = taskText;

  // Toggle done on click
  li.addEventListener("click", function () {
    li.classList.toggle("done");
  });

  // Delete button
  const deleteBtn = document.createElement("button");
  deleteBtn.textContent = "Delete";
  deleteBtn.onclick = function () {
    li.remove();
  };

  li.appendChild(deleteBtn);
  document.getElementById("taskList").appendChild(li);
  input.value = "";
}
