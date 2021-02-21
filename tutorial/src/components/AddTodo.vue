<template>
<div>
    <form @submit="addTodo">
    <input v-model="title">
    <input  type="submit" value="Submit" >
    </form>
</div>
</template>


<script>
export default {
   name:"AddTodoItem",
   data(){
       return {
         title:"",
       }

   },
   methods: {
       addTodo(e){
           e.preventDefault();
           
           const newTodo = {
               title: this.title,
               isCompleted : false
           }
           this.$emit("add-todo", newTodo)
           this.title = "";
       }
   },
}
</script>