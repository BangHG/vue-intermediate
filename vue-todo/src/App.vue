<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput v-on:addTodoItem="addOneItem"></TodoInput>
    <TodoList v-bind:propsdata="todoItems"></TodoList>

    <TodoFooter></TodoFooter>

  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'

export default {
  data:function(){
    return{
    todoItems:[]
    }
  },
  methods:{
    addOneItem:function(todoItem){
      const obj = {completed: false, item: todoItem }
      localStorage.setItem( todoItem,JSON.stringify(obj))
      this.todoItems.push(obj)

    }
  },
  created:function(){
    if(localStorage.length > 0){
      for(var i = 0 ; i < localStorage.length; i ++){
        if(localStorage.key(i) !== 'loglevel:webpack-dev-server'){
          this.todoItems.push(JSON.parse(localStorage.getItem(localStorage.key(i))));
        }
      }
    }
  },

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
  padding:0 20px;
  margin:0;
}

</style>
