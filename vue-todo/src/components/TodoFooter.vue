
<template>
  <div class="clearAllContainer">
    <span class="clearAllBtn" v-on:click="clearTodo">Clear All</span>
  </div>
</template>

<script>
export default {
methods:{
  clearTodo:function(){
    localStorage.clear();
  }
}
}
</script>

<style>
.clearAllBtn{
  background-color: #fff;
  padding: 1em;
  color:#e20303;
  display: block;
  border-radius: 5px;
  cursor: pointer;
  font-weight: 500;

}
.clearAllContainer{  
  max-width: 200px;
  margin:0 auto;
  text-align: center;
}
</style>