<template>
  <form class="row g-3 mt-2 " @submit.prevent="addTodo">
  <div class="col-9 align-items-center">
    <input type="text" class="form-control" v-model="newTodo" placeholder="Input">
  </div>
  <div class="col-3 align-items-center">
    <span class="btn btn-primary mb-3 d-flex align-items-center justify-content-center">
      <i class="fas fa-plus btn-icon"></i>
    </span>
  </div>
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
  } else {
    alert('Please enter a valid todo item.');
  }
}
  }}

</script>

<style>
.form-control {
  width: 100%;
  margin-right: 0px;
}
</style>