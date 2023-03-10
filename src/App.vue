<template>
  <div>
    <nav class="navbar navbar-expand-lg navbar-light bg-light py-3" style="box-shadow: 0px 0px 10px -5px rgba(0,0,0,0.75);">
      <div class="container-fluid justify-content-center align-items-center">
        <a class="navbar-brand " href="#">
          <h1 style="font-weight: bold;">Never forget a task again with the CRUD Todo List experience on Vite VueJS 3.</h1>
        </a>
      </div>
    </nav>

    <div class="container mt-4">
  <todo-list :todos="todos" @toggleComplete="toggleComplete" @deleteTodo="deleteTodo" @addTodo="addTodo"></todo-list>
    </div>
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue'
export default {
  components: {
    TodoList,
  },
  data() {
    return {
      todos: [],
    }
  },
  methods: {
    toggleComplete(index) {
      this.todos[index].completed = !this.todos[index].completed
    },
    deleteTodo(index) {
      this.todos.splice(index, 1)
    },
    addTodo(newTodo) {
      if (newTodo.trim() !== '') {
        this.todos.push({ text: newTodo, completed: false })
      }
    },
  },
}
</script>

<style>
.completed {
  text-decoration: line-through;
}
@media screen and (max-width: 576px) {
  .navbar-brand {
    font-size: 1.2rem;
  }
}

.navbar-brand h1 {
  white-space: normal;
  display: inline-block;
  word-break: break-word;
}

</style>