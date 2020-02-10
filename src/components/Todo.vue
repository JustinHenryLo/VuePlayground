<template>
    <div>
        <h1>Todos</h1>
        <div v-bind:key="todo.id" v-for="todo in param_sample">
        <!-- without the v-bind, it will cause a unique key error -->
        <!-- This iterates all todos, contains all todo cards -->
        <TodoItem v-bind:todo="todo" v-on:del-todo= "$emit('del-todo',todo.id)"/>
        <!-- passing the todo item as todo param in TodoItem -->
        <!-- todo item sent a del-todo signal to todo, todo sends signal del-todo again  -->
        <!-- todo.id item exists because it was passed by todoitem as parameter -->
        </div>
    </div>
    
</template>

<script>
import TodoItem from './TodoItem.vue'
export default {
    name: "Todos" ,
    components:{
        TodoItem
    },
    props: ["param_sample"]
}
</script>

<style scoped>

</style>