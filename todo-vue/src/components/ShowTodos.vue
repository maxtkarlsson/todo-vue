<script setup lang="ts">
import { ref } from "vue";
import { Todo } from "../models/Todo";

const todos = ref<Todo[]>([]);

const userInput = ref("");

const toggleTodoDone = (i: number) => {
  todos.value[i].done = !todos.value[i].done;
};

const addTodo = () => {
  todos.value.push(new Todo(userInput.value, false));
  userInput.value = "";
};

const removeTodo = (i: number) => {
  todos.value.splice(i, 1);
};
</script>

<template>
  <form @submit.prevent="addTodo">
    <input type="text" placeholder="Add todo here" v-model="userInput" />
  </form>

  <ul>
    <li
      v-for="(todo, index) in todos"
      :key="index"
      class="todo"
      :class="todo.done ? 'done' : ''"
    >
      {{ todo.text }}
      <button @click="toggleTodoDone(index)">Toggle</button>
      <button @click="removeTodo(index)">Remove</button>
    </li>
  </ul>
</template>

<style scoped>
.todo {
}

.todo.done {
  text-decoration: line-through;
}
</style>
