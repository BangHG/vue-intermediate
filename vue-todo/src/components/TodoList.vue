<template>
  <div>
    <ul>
      <li v-for="(todoItem, index) in propsdata" v-bind:key="todoItem.item" class="shadow">
        <i class="checkBtn bi bi-square" v-bind:class="{ checkBtnCompleted: todoItem.completed }" v-on:click="toggleComplete(todoItem, index)"> </i>

        <span class="" v-bind:class="{ textCompleted: todoItem.completed }">
          {{ todoItem.item }}
        </span>

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
  props: ['propsdata'],
  // data: function () {
  //   return {
  //     todoItems: []
  // 	}
  // },
  methods: {
    removeTodo: function (todoItem, index) {
      this.$emit('removeItem', todoItem, index);
      console.log(todoItem);
    },

    toggleComplete: function (todoItem, index) {
      console.log(todoItem, index);
      todoItem.completed = !todoItem.completed;
      localStorage.removeItem(todoItem.item); //로컬스토리지는 수정하는 기능이 음슴. 삭제하고 다시 넣어야함. = 갱신
      localStorage.setItem(todoItem.item, JSON.stringify(todoItem));
    },
  },
  //created:  인스턴스 생성시 호출되는 Hook 로직
  // created:function(){
  //   if(localStorage.length > 0){
  //     for(var i = 0 ; i < localStorage.length; i ++){
  //       if(localStorage.key(i) !== 'loglevel:webpack-dev-server'){
  //         // this.todoItems.push(localStorage.key(i))
  //         //devlope. 완수된 것과 키쌍
  //         // const key = localStorage.getItem(localStorage.key(i));
  //         // const parseKey = JSON.parse( key ) //object로 다시 바꾸는 방법 (로컬스토리지의 특성)
  //         // console.log(parseKey)
  //         // this.todoItems.push(parseKey)

  //         this.todoItems.push(JSON.parse(localStorage.getItem(localStorage.key(i))));

  //         // console.log(JSON.parse(localStorage.getItem(localStorage.key(i))))
  //       }
  //     }
  //   }
  // },
};
</script>

<style scoped>
ul {
  list-style-type: none;
  padding-left: 0px;
  margin-top: 0;
  text-align: left;
}
li {
  position: relative;
  display: flex;
  min-height: 50px;
  height: 50px;
  line-height: 50px;
  margin: 0.5rem 0;
  padding: 0 0.9rem;
  background: white;
  border-radius: 5px;
  overflow: hidden;
  padding-right: 50px;
  align-items: center;
}
.checkBtn {
  color: #333;
  margin-right: 0.4em;
  font-size: 1.2em;
}
.checkBtnCompleted:before {
  content: '\f26d' !important;
}
.checkBtnCompleted {
  /* color: #b3adad; */
}
.textCompleted {
  text-decoration: line-through;
  color: #888;
}
.removeBtn {
  position: absolute;
  width: 50px;
  text-align: center;
  right: 0;
  top: 0;
  margin-left: auto;
  background-color: #de4343;
  color: #fff;
}
</style>
