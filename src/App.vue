<template>
  <div id="app">
    <Header/>
    <AddTodo v-on:add-todo="addTodo"/>
    <HelloWorld msg="Hello"/>
    {{name}}
    <Todo v-bind:param_sample="todos" v-on:del-todo="deleteTodo"/><!-- custom component imported in script and components json -->
    <!-- param_sample is passed as prop -->
  </div>
  <!--
      one div only ^
      HelloWorld is a component
      msg is a prop of HelloWold Component 
  -->
</template>


<script>
import HelloWorld from './components/HelloWorld.vue'
import Todo from './components/Todo'
import AddTodo from './components/AddTodo'
import Header from './components/layout/Header.vue'
//no .vue in import
export default {
  name: 'app',
  components: {
    HelloWorld,
    Todo, //<--- Put todo in components
    Header,
    AddTodo
  },
  //data contains all data in page
  //function returning an object
  data(){
    return {
      name: 'Justin',
      todos:[
        {
          id: "Todo Uno",
          title: "Lmao Todo 1",
          completed:false
        },
        {
          id: "Todo Dos",
          title: "Lmao Todo 2",
          completed:false
        },
        {
          id: "Todo Tres",
          title: "Lmao Todo 3",
          completed:false
        },
      ]
    }
  },
  methods:{
    deleteTodo(id){
      //id was passed from the todo component, 
      //MAYBE its positional?
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(todo){
      this.todos.push(todo);
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.btn{
  display: inline-block;
  border:none;
  background: #555;
  color:#fff;
  padding:7px 20px;
  cursor: pointer;
}

.btn:hover{
  background: #666;
}
</style>
