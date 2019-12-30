<template>
  <div id="app">
    <todo-list v-bind:todos="todos"></todo-list>
    <create-todo v-on:add-todo="addTodo"></create-todo>
  </div> 
</template>

<script>
import TodoList from './components/Todo';
import CreateTodo from './components/CreateTodo';

export default {
  components: {
    TodoList,
    CreateTodo,
  },

data() {
    return {
      todos: [{
        title: 'Todo A',
        project: 'Project A',
        done: false,
      }, {
        title: 'Todo B',
        project: 'Project B',
        done: true,
      }, {
        title: 'Todo C',
        project: 'Project C',
        done: false,
      }, {
        title: 'Todo D',
        project: 'Project D',
        done: false,
      }],
    };
  },

  methods: {
    addTodo(title) {
      this.todos.push ({
        title,
        done: false,
      });
    },
  },
};

//o que associa o id <todo-list> v bind (que pelo que eu entendi está associado com export default props todos) com o data? eu vou descobrir isso dps?

</script>

<style>
</style>
