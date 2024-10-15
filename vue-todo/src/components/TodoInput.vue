
<template>
  <div class="inputBox shadow">
    <input type="text" v-model="newTodoItem"/>    
    <span class="addContainer" v-on:click="addTodo">
      <i class="bi bi-plus"></i>
    </span>
  </div>
</template>

<script>
export default {
  data:function(){
    return{
      newTodoItem : ""
    }
  },
  methods:{
    clearInput : function (){
      this.newTodoItem = ''
    },
    addTodo: function(){    
      localStorage.setItem( this.newTodoItem,this.newTodoItem )      
      this.clearInput()      
    }
  }
}
</script>

<style>
input:focus {
	outline: none;
}
.inputBox {
	background: white;
	height: 50px;
  display: flex;
  align-items: center;
  padding: 0 1em;
	border-radius: 5px;
}
.inputBox input {
	border-style: none;
	font-size: 0.9rem;
}
.addContainer {
	float: right;
	background: linear-gradient(to right, #6475FB, #8763FB);
	display: block;	
	border-radius: 0 5px 5px 0;
  height: 100%;
  color:#fff;
  font-size: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
  aspect-ratio: 1;
}
.addBtn {
	color: white;
	vertical-align: middle;
}

</style>