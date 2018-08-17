<template>
  <div>
    <p>{{todo.text}}</p>
    <button @click="clickDelete(todo)">-</button>
  </div>
</template>

<script>
export default {
  name: 'todo-item',
  props: ['todo'],
  methods: {
    clickDelete(todo) {
      this.$emit('delete', todo);
    }
  }
};
</script>
