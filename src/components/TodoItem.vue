<template>
    <div>
        <p>{{todo.title}}</p>
    </div>
</template>

<script>
export default {
    name:"TodoItem",
    props:["todo"],
    data(){
        return{

        }
    }
}
</script>

<style scoped>
    .todo-item{
        background: white;
        padding: 1-px;
        border-bottom: 1px
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