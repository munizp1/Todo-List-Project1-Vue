<template>
  <div class="todo-app">
    <input type="text" v-model="newTodo" @keyup.enter="addTodo" placeholder="Add a new to-do...">
    <ul>
      <li v-for="todo in todos" :key="todo.id">
        {{ todo.text }}
        <button @click="removeTodo(todo.id)">Delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'TodoList',
  data() {
    return {
      newTodo: '',
      todos: [],
      nextId: 1
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim()) {
        this.todos.push({ id: this.nextId++, text: this.newTodo });
        this.newTodo = '';
      }
    },
    removeTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    }
  }
};
</script>

<style scoped>
.todo-app {
  /* Styles here */
}
</style>
