
<template>
  <div>
    <ul>
      <li v-for="todoItem in todoItems" v-bind:key="todoItem">
        {{ todoItem }}


				<span class="removeBtn" v-on:click="removeTodo(todoItem, index)">
          <i class="bi bi-trash3"></i>		
				</span>

      </li>
    </ul>
     <!-- {{ todoItems  }} -->
  </div>
</template>

<script>
export default {

  data: function () {
		return {
			todoItems: []
		}
	},
  //created:  인스턴스 생성시 호출되는 Hook 로직
  created:function(){
    if(localStorage.length > 0){
      for(var i = 0 ; i < localStorage.length; i ++){
        if(localStorage.key(i) !== 'loglevel:webpack-dev-server'){
          this.todoItems.push(localStorage.key(i))
        }
      }
    }
  },



}

</script>

<style>

</style>