<template>
    <div class = "todo-item" v-bind:class="{'is-complete':todo.completed}">
        <p>
            <input type="checkbox" v-on:change="markComplete"/>
            <!-- v-on: is an event caller, change is the event -->
            {{todo.title}}
            <button @click= "$emit('del-todo',todo.id)" class="del">x</button>
            <!-- @click is same as v-on:change -->
            </p>
    </div>
</template>

<script>
export default {
    name:"TodoItem",
    props:["todo"],
    data(){
        return{}
    },
    methods:{
        markComplete(){
            this.todo.completed = !this.todo.completed;
            //todo is the prop, 'this' is the entire todoItem
        }
    }
}
</script>

<style scoped>
    .todo-item{
        background: #f4f4f4;
        padding: 1px;
        margin-bottom: 1px;
    }
    .is-complete{
        text-decoration: line-through;
    }
    .del{
        background: red;
        color:white;
        border: none;
        padding: 5px 9px;
        border-radius: 50%;
        cursor: pointer;
        float: right;
    }
</style>