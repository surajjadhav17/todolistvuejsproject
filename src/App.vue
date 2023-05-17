<template>
<div id="app">
<h1 class="head">Todo App</h1>


<form @submit.prevent="addNewTodo">
  <div class="form-group">
  <label for="newTodo"><h5>New Todo</h5></label>
  
<div class="head d-flex mb-5 mt-0">
  <input v-model="newTodo" type="text" class="form-control" id="usr" name="newTodo">

  <button  type="submit" class="btn btn-primary ml-2">Add </button>
</div>
</div>


</form>
<h3>Todo List..</h3>
<div>
  <ol v-for="(todo,index) in todos" :key="todo.id">
    <li class="d-flex justify-content-between" >
      <h4 :class="{done: todo.done}" @click="toggleDone(todo)">{{ todo.content }}</h4>
      <button type="submit" class="btn btn-sm btn-danger" @click="remove(index)">Delete</button>

    </li>
  </ol>
</div>
</div>
</template>

<script>
import {ref} from 'vue';

export default {
 setup(){
  const newTodo = ref('');
  const todos=ref([]);


  function addNewTodo(){
    todos.value.push({
      id:Date.now(),
      done:false,
      content:newTodo.value,
    })
   console.log(newTodo.value);
   newTodo.value='';
  }


  function toggleDone(todo){
    todo.done=!todo.done;

  }

  function remove(i){
    this.todos.splice(i,1)
  }


  return{
    todos,
    newTodo,
    addNewTodo,
    toggleDone,
    remove
    

  }
 }}
</script>

<style>
#app{
  margin: auto;
width:70%;
height: 700px;
margin-top:25px;
/* border: 1px solid red;  */
background-color: rgb(243, 208, 119);
}

.head{
  text-align: center;
}

.done{
  text-decoration: line-through;
}


</style>
