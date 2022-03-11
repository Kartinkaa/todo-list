<template>
  <ul>
    <TodoItem
      v-for="(todo, i) of todos"
      v-bind:todo="todo"
      v-bind:key="i"
      v-on:remove-todo="removeTodo"
    />
  </ul>
</template>

<script>
import TodoItem from "@/components/TodoItem";
export default {
  props: ["todos"],
  components: {
    TodoItem,
  },
  methods: {
    removeTodo(id) {
      this.$emit("remove-todo", id);
    },
  },
};
</script>

<style scoped>
ul {
  list-style: none;
  padding: 0;
  width: 50%;
  margin: auto;
}
</style>
