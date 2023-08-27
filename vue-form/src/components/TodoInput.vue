<template>

  <div class="inputBox shadow">
    <input type="text" v-model="todoItem" @keyup.enter="addTodo">
    <span class="addContainer" @click="addTodo">
      <i class="material-icons addBtn">add</i>
    </span>
  </div>

</template>

<script>
export default {
  data: function () {
    return{ todoItem:''}
  }
  ,
  methods: {
    addTodo: function () {
      if (this.todoItem ){
        this.$emit('addOne',this.todoItem);
        console.log(this.todoItem);
        this.clearInput();
        
      }
    },
    clearInput() {
      this.todoItem = '';
    }
  }
}
</script>
<style scoped>
input:focus {
  outline: none;
}

.inputBox {
  display: flex;
  background: white;
  height: 50px;
  width:50%;
  margin: auto;
  line-height: 50px;
  border-radius: 5px;
}

.inputBox input {
  width: 93%;
  border-style: 1px solid black;
  font-size: 0.9rem;
}

.addContainer {
  float: right;
  background: linear-gradient(to right, #62EAC6, #32CEE6);
  display: block;
  width: 3rem;
  border-radius: 0 5px 5px 0;
}

.addBtn {
  color: white;
  vertical-align: middle;
}</style>