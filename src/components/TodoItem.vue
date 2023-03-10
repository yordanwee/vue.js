<template>
  <li :class="{ completed }" class="list-group-item d-flex justify-content-between border-0 mb-2 rounded"
      :style="computedStyles" @click="toggleComplete">
      <div class="d-flex align-items-center">
  <input class="form-check-input me-2" type="checkbox" :checked="completed" aria-label="..." />
  <span class="fs-6">{{ todo.text }}</span>
</div>
<a @click="deleteTodo" data-mdb-toggle="tooltip" title="Remove item">
  <i class="fas fa-trash delete-icon animate__animated animate__bounceIn" :class="{ 'animated': completed }" :style="{ color: completed ? '#fff' : '#0d6efd' }"></i>
</a>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      completed: this.todo.completed,
    }
  },
  computed: {
    computedStyles() {
      return {
        backgroundColor: this.completed ? '#0d6efd' : '#f4f6f7',
        boxShadow: this.completed ? 'rgba(13, 110, 253, 0.25) 0px 8px 24px' : '',
        color: this.completed ? '#fff' : '',
      };
    },
  },
  methods: {
    toggleComplete() {
      this.completed = !this.completed
      this.$emit('toggleComplete')
    },
    deleteTodo() {
      this.$emit('deleteTodo')
    },
  },
}
</script>

<style scoped>
li {
  background-color: #fff;
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.06), 0 2px 4px rgba(0, 0, 0, 0.06), 0 4px 8px rgba(0, 0, 0, 0.06),
    0 8px 16px rgba(0, 0, 0, 0.06), 0 16px 32px rgba(0, 0, 0, 0.06), 0 32px 64px rgba(0, 0, 0, 0.06);
  transition: all 0.3s ease-in-out;
}

.completed {
  text-decoration: line-through;
  opacity: 0.5;
}

li:hover {
  transform: scale(1.05);
}

@media (max-width: 576px) {
  li {
    font-size: 0.9rem;
  }
}

.delete-icon {
  position: relative;
  animation: trash 1s ease-in-out;
}

@keyframes trash {
  0% {
    transform: rotate(0deg);
  }
  50% {
    transform: rotate(15deg);
  }
  100% {
    transform: rotate(-15deg);
  }
}

</style>