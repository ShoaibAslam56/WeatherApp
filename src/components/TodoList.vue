<template>
    <div id="maindiv">
        <div class="todo-container">
      <h1>📝 Stylish Todo List</h1>
      <div class="todo-input-container">
        <input v-model="newTask" placeholder="Enter a new task" class="todo-input" />
        <button @click="addTask" class="todo-add-btn">
          <i class="fa fa-plus"></i> Add Task
        </button>
      </div>
      <ul class="todo-list">
        <li v-for="(item, index) in task" :key="index" class="todo-item">
          <span class="task-text">{{ item }}</span>
          <button @click="removeTask(index)" class="todo-remove-btn">
            <i class="fa fa-trash"></i>
          </button>
        </li>
      </ul>
    </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        newTask: "",
        task: [],
      };
    },
    created() {
      let savedTasks = localStorage.getItem("task");
      if (savedTasks) {
        this.task = JSON.parse(savedTasks);
      }
    },
    methods: {
      addTask() {
        if (this.newTask.trim()) {
          this.task.push(this.newTask.trim());
          this.newTask = "";
          this.saveTasksLocal();
        }
      },
      removeTask(index) {
        this.task.splice(index, 1);
        this.saveTasksLocal();
      },
      saveTasksLocal() {
        localStorage.setItem("task", JSON.stringify(this.task));
      },
    },
  };
  </script>
  
  <style>
  #maindiv {
    font-family: Arial, sans-serif;
    background-color: black;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .todo-container {
    max-width: 400px;
    padding: 20px;
    background: #ffffff;
    border-radius: 8px;
    box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.1);
    text-align: center;
  }
  
  .todo-container h1 {
    font-size: 24px;
    color: #333;
    margin-bottom: 20px;
  }
  
  .todo-input-container {
    display: flex;
    gap: 10px;
  }
  
  .todo-input {
    flex: 1;
    padding: 10px;
    font-size: 16px;
    border: 2px solid #007bff;
    border-radius: 5px;
    outline: none;
  }
  
  .todo-input:focus {
    border-color: #0056b3;
  }
  
  .todo-add-btn,
  .todo-remove-btn {
    background-color: #007bff;
    color: white;
    border: none;
    border-radius: 5px;
    padding: 10px 15px;
    font-size: 14px;
    cursor: pointer;
    display: flex;
    align-items: center;
    gap: 5px;
  }
  
  .todo-add-btn:hover {
    background-color: #0056b3;
  }
  
  .todo-remove-btn {
    background-color: #dc3545;
  }
  
  .todo-remove-btn:hover {
    background-color: #b02a37;
  }
  
  /* Task List */
  .todo-list {
    list-style: none;
    padding: 0;
    margin: 20px 0;
  }
  
  .todo-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: #f1f1f1;
    margin: 10px 0;
    padding: 10px 15px;
    border-radius: 5px;
  }
  
  .task-text {
    font-size: 16px;
    color: #333;
  }
  </style>
  