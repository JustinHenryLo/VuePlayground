<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    
    
  </div>
</template>
//msg is being passed as a prop

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
// scoped means that the css here does not apply to all other components
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
