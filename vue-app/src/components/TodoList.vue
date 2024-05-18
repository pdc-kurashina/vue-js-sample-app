<template>
  <div>
    <h1>Todo List</h1>
    <form @submit.prevent="addTodo">
      <input v-model="newTodo" placeholder="What needs to be done?" />
      <button type="submit">Add</button>
    </form>
    <ul>
      <TodoItem v-for="todo in todos" :key="todo.id" :todo="todo" @toggle-completed="toggleCompleted" />
    </ul>
  </div>
</template>

<script>
import TodoItem from './TodoItem.vue'

export default {
  name: 'TodoList',
  components: {
    TodoItem
  },
  data() {
    return {
      newTodo: '',
      todos: []
    }
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim()) {
        this.todos.push({
          id: Date.now(),
          text: this.newTodo.trim(),
          completed: false
        });
        this.newTodo = '';
      }
    },
    toggleCompleted(todoId) {
      const todo = this.todos.find(todo => todo.id === todoId);
      if (todo) {
        todo.completed = !todo.completed;
      }
    }
  }
}
</script>

<style scoped>
form {
  margin-bottom: 20px;
}
</style>
