<template>
    <div class="todo-app">
      <input class="todo-input" type="text" v-model="newTodoTitle" @keyup.enter="addTodo" placeholder="Add new todo...">
      <ul>
        <li v-for="todo in todos" :key="todo.id" class="todo-item">
          <span :class="{ 'completed': todo.completed }" @click="toggleTodoCompletion(todo.id)">{{ todo.title }}</span>
          <button class="delete-btn" @click="deleteTodo(todo.id)">Delete</button>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    name: 'TodoList',
    data() {
      return {
        newTodoTitle: '',
        todos: [
          { id: 1, title: 'Learn Vue', completed: false },
          { id: 2, title: 'Build a Todo App', completed: false }
        ]
      };
    },
    methods: {
      addTodo() {
        if (this.newTodoTitle.trim()) {
          const newTodo = {
            id: this.todos.length + 1,
            title: this.newTodoTitle,
            completed: false
          };
          this.todos.push(newTodo);
          this.newTodoTitle = '';
        }
      },
      toggleTodoCompletion(id) {
        const todo = this.todos.find(todo => todo.id === id);
        if (todo) {
          todo.completed = !todo.completed;
        }
      },
      deleteTodo(id) {
        this.todos = this.todos.filter(todo => todo.id !== id);
      }
    }
  };
  </script>
  
  <style scoped>
  /* Insert the CSS provided earlier here */
  /* Container styling */
.todo-app {
  max-width: 400px;
  margin: 50px auto;
  padding: 20px;
  background-color: #f5f5f5;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

/* Input field styling */
.todo-input {
  width: 100%;
  padding: 10px;
  margin-bottom: 20px;
  border: 2px solid #ccc;
  border-radius: 4px;
  font-size: 16px;
}

/* Todo item styling */
.todo-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 10px;
  margin-bottom: 10px;
  background-color: #fff;
  border-radius: 4px;
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.05);
}

.todo-text {
  font-size: 16px;
}

/* Button styling */
.button {
  padding: 5px 10px;
  font-size: 14px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.add-btn {
  background-color: #007bff;
  color: #fff;
}

.add-btn:hover {
  background-color: #0056b3;
}

.delete-btn {
  background-color: #dc3545;
  color: #fff;
}

.delete-btn:hover {
  background-color: #c82333;
}

/* Optional: styling for completed todos */
.completed {
  text-decoration: line-through;
  color: #6c757d;
}

  </style>
  