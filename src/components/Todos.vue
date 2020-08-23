<template>
  <div>
    <!-- when we loop thru we need a unique key attached to it, hence bind key -->
    <div v-bind:key="todo.id" v-for="todo in todos">
      <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo',todo.id)"/>
    </div>
  </div>
</template>

<script>
import TodoItem from "./TodoItem";
export default {
  name: "Todos",
  components: {
    TodoItem,
  },
  // accepting prop passed from parent component app.vue
  props: ["todos"],
};
</script>

<style scoped>
</style>