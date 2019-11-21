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

export default {
  name: 'app',
  components: {
    Todos,
    Header,
    AddTodo
  },
  data(){
    return{
      todos:[
        {
          id:1,
          title:"Todo One",
          completed:false
        },
        {
          id:3,
          title:"Todo Two",
          completed:true
        },
        {
          id:2,
          title:"Todo Three",
          completed:false
        }
      ]
    }
  },
  methods:{
    deleteTodo(id){
      this.todos = this.todos.filter(todo=>todo.id!== id);
    },
    addTodo(newTodo){
      this.todos = [...this.todos,newTodo];
    }
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
