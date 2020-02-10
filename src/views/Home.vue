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
import HelloWorld from '../components/HelloWorld.vue'
import Todo from '../components/Todo'
import AddTodo from '../components/AddTodo'
import Header from '../components/layout/Header.vue'
import axios from 'axios';
//no .vue in import
export default {
  name: 'Home',
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
      todos:[]
    }
  },
  methods:{
    deleteTodo(id){
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      //id was passed from the todo component, 
      //MAYBE its positional?
      .then(this.todos = this.todos.filter(todo => todo.id !== id))
      
    },
    addTodo(todo){
      const { title, completed } = todo;
      //const constructs title and completed variable from todo.title and todo.completed
      axios.post('https://jsonplaceholder.typicode.com/todos',{
        title,
        completed
      })
      //ES6 schortcut for {title:title, completed:completed}
      .then(res => this.todos.push(res.data))
      //you do this because sending post will give back new ID
    }
  },
  //this will run on start
  //we will use axios in here (Http library to make requests)
  //npm i axios
  created(){
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
    //get usually has a promise function like this
    .then(res =>this.todos = res.data)
    //>>study this syntax
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
