<template>
    <div>
        <h1>Todos</h1>
        <div v-bind:key="todo.id" v-for="todo in param_sample">
        <!-- without the v-bind, it will cause a unique key error -->
        <!-- This iterates all todos, contains all todo cards -->
        <TodoItem v-bind:todo="todo"/>
        <!-- passing the todo item as todo param in TodoItem -->
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