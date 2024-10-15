<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput></TodoInput>
    <TodoList></TodoList>
    <TodoFooter></TodoFooter>

  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'

export default {
  components:{
    'TodoHeader' :TodoHeader,
    'TodoInput' :TodoInput,
    'TodoList' : TodoList,
    'TodoFooter' :TodoFooter,
  }
}  
</script>


<style>

@import url('https://fonts.googleapis.com/css2?family=Ubuntu:ital,wght@0,300;0,400;0,500;0,700;1,300;1,400;1,500;1,700&display=swap');
@import url("https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css");


html,body{
  font-family: 'Ubuntu', sans-serif;
}
body{
  background-color: #f6f6f6;
  text-align: left;
}

</style>
