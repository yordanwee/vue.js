<template>
  <form class="row g-3 mt-2 " @submit.prevent="addTodo">
  <div class="col-9 align-items-center">
    <input type="text" class="form-control" v-model="newTodo" placeholder="Input">
  </div>
  <button class="col-3 align-items-center m-0 p-0 bg-transparent border-0 mt-3">
    <span class="btn btn-primary d-flex align-items-center justify-content-center" style="padding: 10px 0">
      <i class="fas fa-plus btn-icon"></i>
    </span>
  </button>
</form>
</template>

<script>
export default {
  data() {
    return {
      newTodo: '',
    }
  },
  methods: {
    addTodo() {
  if (this.newTodo.trim() !== '') {
    this.$emit('addTodo', this.newTodo);
    this.newTodo = '';
  }
}
  }}

</script>

<style>
.form-control {
  width: 100%;
  margin-right: 0;
}
</style>