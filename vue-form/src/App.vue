<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput v-on:addOne="addFn"></TodoInput>
    <TodoList v-bind:propsdata="todos"
    v-on:removeOne="removeFn"
    v-on:toggleOne="toggleFn"></TodoList>
    <TodoFooter v-on:clearOne="clearFn"></TodoFooter>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'

export default {
  data: function(){
    return { todos : []}
  },
  methods: {
    addFn(todoItem) {
      var obj = { completed: false, item: todoItem };
      localStorage.setItem(todoItem, JSON.stringify(obj));
      this.todos.push(obj);
    },


    removeFn(todo, index) {
      localStorage.removeItem(todo.item);
      this.todos.splice(index, 1);
   
    },
    toggleFn(todo, index) {
      this.todos[index].completed = !this.todos[index].completed
      localStorage.removeItem(todo.item);
      localStorage.setItem(todo.item, JSON.stringify(todo));
    },
    clearFn() {
      localStorage.clear();
      console.log(this.todos);
      this.todos = [];
    },

    },
        created() {
    if (localStorage.length > 0) {
      for (let i = 0; i < localStorage.length; i++) {
        if (localStorage.key(i) !== 'loglevel:webpack-dev-server') {
          console.log(localStorage.getItem(localStorage.key(i)));
          this.todos.push(JSON.parse(localStorage.getItem(localStorage.key(i))));
        }
      }
    }
  },

  components: {
    TodoHeader,
    TodoInput,
    TodoList,
    TodoFooter
  }
}
</script>
