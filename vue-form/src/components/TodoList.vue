<template>
  <div class="list">
    <ul>
      <li v-for="(todoItem, index) in propsdata" v-bind:key="todoItem" class="shadow">
        <span class="checkBtn material-icons" v-bind:class="{ checkBtnCompleted: todoItem.completed }"
          v-on:click="toggleFn(todoItem, index)">done</span>
        <span v-bind:class="{ textCompleted: todoItem.completed }">{{ todoItem.item }}</span>
        <span class="removeBtn" v-on:click="removeFn(todoItem, index)">
          <i class="material-icons">delete</i>
        </span>
      </li>
    </ul>
  </div>
</template>

<script>
    export default {
       props:['propsdata'],

       methods:{
        removeFn(todo,index){
            this.$emit('removeOne',todo,index);
        },
        toggleFn(todo,index){
            this.$emit('toggleOne',todo,index);
        }
     }     
    }
</script>
<style>
.list{
  justify-content: center;
  display: flex;
}

.checkBtn {
  line-height: 45px;
  color: #62acde;
  margin-right: 5px;
}
.checkBtnCompleted {
  color: #b3adad;
}
.textCompleted {
  text-decoration: line-through ;
  color: #b3adad;
}
.removeBtn {
  margin-left: auto;
  color: #de4343;
}
</style>
