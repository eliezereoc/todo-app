<template>
  <div>
    <h1>Todo-app</h1>
  </div>
  <div v-if="!editMode">
    <Button @click="newTodo">Novo</Button>
    <todo-list ></todo-list>
  </div>
  <div>     
    <todo-item v-if="editMode" @cancel="cancel" @salveTodo="salveTodo"></todo-item>
  </div>
</template>

<script>
 import TodoList from './components/TodoList.vue';
 import TodoItem from './components/TodoItem.vue';

export default {
  components: {
    TodoList,
    TodoItem
  },
  data() {
    return {
      editMode: false,
      todos: []
    }
  },
  methods: {
    newTodo() {
      this.editMode = true
    },
    cancel() {
      this.editMode = false;
    },
    salveTodo(todo) {
      this.todos.push(todo);
      localStorage.setItem('todos', JSON.stringify( this.todos));
    }
  }
}
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif; 
    color: #2c3e50;  
  }
</style>
