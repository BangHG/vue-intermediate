
<template>
  <div class="inputBox shadow">
    <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo"/>
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
    addTodo: function(){
      if (this.newTodoItem !== ''){
        const obj = {completed: false, item: this.newTodoItem }
        // localStorage.setItem( this.newTodoItem,this.newTodoItem )
        // localStorage.setItem( this.newTodoItem,obj )
        localStorage.setItem( this.newTodoItem,JSON.stringify(obj) )
        this.clearInput()
      }
    },

    clearInput : function (){
      this.newTodoItem = ''
    },
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
  position: relative;
}
.inputBox input {
	border-style: none;
	font-size: 0.9rem;
  width: 100%;
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
  position: absolute;right:0;top:0;
}
.addBtn {
	color: white;
	vertical-align: middle;
}

</style>