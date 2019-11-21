<template>
  <div id="app">
    <Todos />
  </div>
</template>

<script>
import Todos from './components/Todos'

export default {
  name: 'app',
  components: {
    Todos
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
          completed:false
        },
        {
          id:2,
          title:"Todo Three",
          completed:false
        }
      ]
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
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
