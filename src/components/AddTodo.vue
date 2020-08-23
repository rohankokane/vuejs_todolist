<template>
  <div>
    <form @submit.prevent="addTodo">
      <!-- v-model two way binding between form input and app state -->
      <input type="text" v-model="title" name="title" placeholder="Add Todo...">
      <input type="submit" value="Submit" class="btn">
    </form>
  </div>
</template>

<script>
// json placeholder gives an id
// import {v4 as uuid} from "uuid";
// import { v4 as uuidv4 } from 'uuid';
export default {
  name: "AddTodo",
  data() {
    return {
      title: ''
    }
  },
  methods: {
    addTodo(e) {
        e.preventDefault();  
        const newTodo = {
            // id:uuid.v4(),
            // id: uuidv4(),
            title: this.title,
            completed: false
        }
      // Send up to parent
      this.$emit('add-todo', newTodo);
      this.title = '';
    }
  }
}
</script>

<style scoped>
  form {
    display: flex;
  }
  input[type="text"] {
    flex: 10;
    padding: 5px;
  }
  input[type="submit"] {
    flex: 2;
  }
</style>

