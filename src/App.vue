<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
import Todos from './components/Todos'
import AddTodo from './components/AddTodo'
import Header from './components/layout/Header'
import axios from 'axios';

export default {
  name: 'app',
  components: {
    Todos,
    Header,
    AddTodo
  },
  data(){
    return{
      todos:[]
    }
  },
  methods:{
    deleteTodo(id){
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(this.todos.filter(todo=>todo.id!== id))
      .catch(err => alert(err));

    },
    addTodo(newTodo){
      const {title , completed} = newTodo;
      axios.post('https://jsonplaceholder.typicode.com/todos',{
        title,
        completed
      })
      .then(res => this.todos = [...this.todos,res.data])
      .catch(err => alert(err))

    }
  },
  created(){
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
    .then(res => this.todos = res.data)
    .catch(err => alert(err));
  }
}
</script>

<style>
  *{
    box-sizing:border-box;
    margin:0;
    padding:0;
  }

  body {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
  }
  .btn{
    display:inline-block;
    border:none;
    background: #555;
    color:#fff;
    padding:7px 20px;
    cursor:pointer;
  }
  .btn:hover{
    background:#666
  }
</style>
