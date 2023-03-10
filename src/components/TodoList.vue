<template>
  <section class="bg-transparent">
    <div class="container py-5">
      <h3 class="text-muted text-center mb-5 fw-bold" style="margin-top: -20px">Maximize your productivity and never forget a task again!</h3>
      <div class="row justify-content-center">
        <div class="col-md-8 col-lg-6">
          <div class="card border-0 rounded-3 shadow-lg">
            <div class="card-body p-5">
              <h2 class="mb-3">Todo List</h2>
              <todo-item v-for="(todo, index) in todos" :key="index" :todo="todo" @toggleComplete="toggleComplete(index)"
                @deleteTodo="deleteTodo(index)"></todo-item>
              <todo-form @addTodo="addTodo"></todo-form>
            </div>
          </div>
          <footer class="d-flex justify-content-center align-items-center mt-5 pt-4">
            <div>
            <p class="text-muted fst-italic text-center">"Get it done, have some fun!"</p>
            <p class="text-muted text-center">Made with ❤️ by Kelompok 3</p>
              <p class="text-muted text-center" style="font-size: 12px">© 2023 . All Rights Reserved.</p>
            </div>
          </footer>
        </div>
      </div>
    </div>
  </section>
</template>


<script>
import TodoItem from './TodoItem.vue'
import TodoForm from './TodoForm.vue'

export default {
  components: {
    TodoItem,
    TodoForm,
  },
  props: {
    todos: {
      type: Array,
      required: true,
    },
  },
  methods: {
    toggleComplete(index) {
      this.$emit('toggleComplete', index)
    },
    deleteTodo(index) {
      this.$emit('deleteTodo', index)
    },
    addTodo(newTodo) {
      this.$emit('addTodo', newTodo)
    },
  },
}
</script>