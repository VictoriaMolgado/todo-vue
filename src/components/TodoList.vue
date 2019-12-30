<template>
  <todo v-on:delete-todo="deleteTodo" v-for="todo in todos" v-bind:todo="todo"></todo>
</template>

<script type="text/javascript">
export default {
  props: ["todos"],

  methods: {
    deleteTodo(todo){
      const todoIndex = this.todos.indexOf(todo);
      this.todos.splice(todoIndex, 1);
    },

    completeTodo(todo){
        const todoIndex = this.todos.indexOf(todo);
        this.todos[todoIndex].done = true;
    },
  },
};
</script>

<style>
</style>

