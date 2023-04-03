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

<template></template>

<style scoped></style>
