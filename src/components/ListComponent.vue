<template>
  <form class="todo-form" action="" @submit.prevent="addItems">
    <input
      class="todo-input"
      type="text"
      v-model="todoInput"
      placeholder="Enter the todo item"
    />
    <button class="submit-button">Submit</button>
  </form>
  <transition-group name="list" tag="ul" class="todo-list">
    <li v-for="(todo, i) in toDoItems" :key="todo" class="todo-item">
      <button @click="removeItems(i)" class="remove-button">X</button>
      {{ todo }}
    </li>
  </transition-group>
</template>

<script setup>
import { ref } from "vue";
const todoInput = ref("");
console.log(todoInput.value);
const toDoItems = ref([
  "learn Js",
  "learn nodejs",
  "learn ASP.net",
  "learn Python",
]);

const addItems = () => {
  toDoItems.value.unshift(todoInput.value); //unshift puts value on the top
  todoInput("");
};

const removeItems = (index) => {
  toDoItems.value.splice(index, 1);
};
</script>

<style>
.list-move,
.list-enter-active,
.list-leave-active {
  transition: all 0.5s ease;
}

.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateX(-50px);
}
.list-leave-active {
  position: absolute;
}

/* css style */
.todo-form {
  width: 500px;
  margin: 0 auto;
}

.todo-input {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  box-sizing: border-box;
  border: 2px solid #ccc;
  border-radius: 4px;
}

.todo-title {
  text-align: center;
  margin: 16px 0;
}

.submit-button {
  width: 100%;
  background-color: #4caf50;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.todo-list {
  list-style-type: none;
  padding: 0;
  margin: 0;
}

.todo-item {
  padding: 12px;
  border-bottom: 1px solid #ccc;
  text-align: left;
}

.remove-button {
  float: right;
  background-color: #f44336;
  color: white;
  padding: 5px 10px;
  border-radius: 50%;
  cursor: pointer;
}
</style>
