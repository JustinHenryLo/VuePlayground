<template>
    <div>
        <form @submit="addTodo">
            <input type ="text" v-model="title" name="title" placeholder="Add Todo...">
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>

<script>
//import uuid from 'uuid';
export default {
    name:"AddTodo",
    data(){
        return{
            title:''
        }
    },
    methods:{
        addTodo(e){
            //prevent default stops the submit action, we dont really want to submit
            e.preventDefault();

            //npm install uuid
            //this is used to emulate mongo db giving unique ids
           //uuid.v4 generates a unique id, v4 is just version
           var newTodo = {
                //id:uuid.v4(), - this was needed to generate id but now its not needed because jsonplaceholder gives an id if you make a request
                title:this.title,
                completed: false
            }
            this.$emit('add-todo',newTodo);
            this.title = "";
        }
    }
}
</script>
<style scoped>
    form{
        display:flex;
    }
    input[type="text"]{
        flex:10;
        padding:5px;
    }
    input[type="submit"]{
        flex:2;
        padding:5px;
    }
</style>