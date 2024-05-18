<template>
  <li>
    <input type="checkbox" :checked="todo.completed" @change="toggleCompleted" />
    <span :class="{ 'completed': todo.completed }">{{ todo.text }}</span>
  </li>
</template>

<script>
export default {
  name: 'TodoItem',
  props: {
    todo: {
      type: Object,
      required: true
    }
  },
  methods: {
    toggleCompleted() {
      this.$emit('toggle-completed', this.todo.id);
    }
  }
}
</script>

<style scoped>
.completed {
  text-decoration: line-through;
}
</style>
