<template>
  <div id="app">
    <HelloWorld msg="Hello"/>
    {{name}}
    <Todo/><!-- custom component imported in script and components json -->
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
//no .vue in import
export default {
  name: 'app',
  components: {
    HelloWorld,
    Todo //<--- Put todo in components
  },
  //data contains all data in page
  //function returning an object
  data(){
    return {
      name: 'Justin',
      todos:[
        {
          id: "Todo Uno",
          title: "Lmao Todo",
          completed:false
        },
        {
          id: "Todo Dos",
          title: "Lmao Todo",
          completed:false
        },
        {
          id: "Todo Tres",
          title: "Lmao Todo",
          completed:false
        },
      ]
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
</style>
