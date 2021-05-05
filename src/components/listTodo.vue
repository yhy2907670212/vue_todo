<template>
  <div class="todo-lis">
    <listItemTodo 
    v-for="todo in todos" 
    :key="todo.id" 
    :todo-item="todo"
    @change-state="todo.completed = $event.target.checked" />
  </div>
</template>

<script>
import listItemTodo from "./listItemTodo";
export default {
  name: "listTodo",
  components: {
    listItemTodo,
  },
  props: ["todos"],
};
</script>

<style>
.todo-list {
  display: grid;
  row-gap: 14px;
}
</style>