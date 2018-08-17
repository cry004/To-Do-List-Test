<template>
  <div class="app">
    <h1>Vue to do</h1>
    <div class="container">
      <div class="todo_content">
        <apptodoitem v-for="todo in toDolist" :todo="todo" :key="todo.id" @delete="onclickDelete"></apptodoitem>
      </div>
      <input type="text" v-model="todo" @keyup.enter="clickAdd()">
      <button @click="clickAdd()">+</button>
    </div>
  </div>
</template>

<script>
import toDoitem from './components/toDoitem.vue';
export default {
  name: 'todo-list',
  data() {
    return {
      toDolist: [{ id: 1, text: 'AAAAA' }, { id: 2, text: 'BBB' }],
      todo: ''
    };
  },
  components: {
    apptodoitem: toDoitem
  },
  methods: {
    clickAdd() {
      if (!this.todo) {
        alert('Please enter a todo!');
        return;
      }
      const newid =
        Math.max.apply(
          Math,
          this.toDolist.length > 0 ? this.toDolist.map(t => t.id) : [0]
        ) + 1;
      this.toDolist.push({ id: newid, text: this.todo });
      this.todo = '';
    },
    onclickDelete(todo) {
      this.toDolist = this.toDolist.filter(item => item != todo);
    }
  }
};
</script>

<style>
</style>
