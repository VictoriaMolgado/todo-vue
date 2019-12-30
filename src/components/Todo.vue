// the template area is the visual part of a component
// Behaviour, events and data storage for the template are handled by the class. 
<template>
 <div>
        <ul>
            <li> Todo A </li> 
            <li> Todo B </li> 
            <li> Todo C </li> 
        </ul> 
    
    <p>Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
    <p>Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>
    <todo  v-for="todo in todos" v-bind:todo="todo"></todo>
    <todo v-on:delete-todo="deleteTodo" v-on:complete-todo="completeTodo" v-for="todo in todos" :todo.sync="todo"></todo>
    <div class='ui centered card' v-for="todo in todos">
         <div class='content' v-show="!isEditing">
            <div class='header'>
            {{ todo.title }}
            </div>
            <div class='meta'>
            {{ todo.project }}
            </div>
            <div class='extra content'>
                <span class='right floated edit icon' v-on:click="showForm"> 
                    <i class='edit icon'></i> 
                </span>
                <span class='right floated trash icon' v-on:click="deleteTodo(todo)">
                    <i class='trash icon'></i>
                </span>
            </div>
        </div>
    <div class='content' v-show="isEditing"> 
        <div class='ui form'>
                <div class='field'> 
                     <label>Title</label>
                     <input type='text' v-model="todo.title">
                </div>
                <div class='field'>
                    <label>Project</label>
                    <input type='text' v-model="todo.project">
                </div>
                <div class='ui two button attached buttons'>
                    <button class='ui basic blue button' v-on:click="hideForm">
                        Close X 
                    </button>
                </div>
        </div>
    </div>

        <div class='ui bottom attached green basic button' v-show="!isEditing &&todo.done" disabled>
            Completed
        </div>
        <div class='ui bottom attached red basic button' v-show="!isEditing && !todo.done">
            Complete
        </div>
    </div>
</div>
</template>

<script type="text/javascript">

import Todo from './Todo';
// eu não estava importando isso antes em lugar nenhum, como estava funcionando e por que o tutorial chama de refatorar? 

export default {
    props: ['todos'],
    // eu apaguei o que chamava o componente aqui e o negócio continuou funcionando ???? pq
   data() {
    return {
      isEditing: false,
    };
  },
  methods: {
    showForm() {
      this.isEditing = true;
    },
    hideForm() {
      this.isEditing = false;
    },
     
    deleteTodo(todo){
      this.$emit('delete-todo', todo);
    },

    completeTodo(todo){
        this.$emit('complete-todo', todo);
    },
  },
};

</script>

// não entendo porque o complete não está funcionando, apesar de ter quase certeza que o erro está nele