<template>
<div class="container">
    <div class="row">
        <div class="col-12">
           <p class="display-3"> Vue Crash Course</p>
        </div>
    </div>
    <br>
    <div class="row">
        <Newtodo @on-addtodo="addToDo($event)"/>
    </div>
    <div class="row">
        <div class="col-12 col-lg-6">
            <ul class="list-group">
              <Todo 
              v-for="(todo, index) in todos" 
              :key="index" 
              :todoString = todo.todoString
              :completed = todo.completed
              @on-delete="deleteToDo(todo)"
              @on-toggle="toggleToDo(todo)"
              @on-edit="editToDo(todo, $event)"
              />
            </ul>
        </div>
    </div>
</div>
</template>

<script>
import Todo from "./Todo";
import Newtodo from "./newTodo.vue";
export default {
    components: {
        Todo,
        Newtodo
    },
    data(){
        return{
            todos:[
                {todoString:"Comlete the vue.js crash course", completed:false},
                {todoString:"Have a coffe", completed:true},
                {todoString:"get fresh", completed:false},
                {todoString:"have a bath", completed:false},
                {todoString:"smoke some ciggates", completed:false}
            ]
        }
    },
    methods:{
        addToDo(newToDo){
            this.todos.push({
                todoString:newToDo,
                completed:false
            });
        },
        toggleToDo(todo){
            todo.completed = !todo.completed;
        },
        editToDo(todo,newtodoString){
            todo.todoString = newtodoString;
        },
        deleteToDo(deleteToDo){
            this.todos = this.todos.filter( todo => todo.todoString !== deleteToDo.todoString );
        }
    }
};
</script>

<style>

</style>
