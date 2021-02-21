<template>
  <div id="app">

    <Header />
    <add-todo v-on:add-todo="addTodo"/>
    <todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
import Todos from './components/Todos.vue';
import Header from './components/Header'
import AddTodo from './components/AddTodo.vue';
import axios from 'axios'
export default {
  name: "App",
  components: {Todos, Header, AddTodo},
  data() {
    return {
      todos: [
      ],
    };
  },
  methods:{
    deleteTodo(id){
        this.todos.splice(id-1,1)
    },
    addTodo(newTodo){
      const {title,completed} = newTodo;
      axios.post("https://jsonplaceholder.typicode.com/todos", {
        title,
        completed
      }).then(res => {
      this.todos = [...this.todos, res.data]
      }).catch(err => console.log(err))
    }
  },
  created(){
    axios.get("https://jsonplaceholder.typicode.com/todos?_limit=20")
    .then(res => {
      this.todos = res.data
    }).catch(err => {
      console.log(err)
    })
  }
};
</script>

<style>
</style>
