<template>
  <div id="myDIV" class="header">
    <h2 style="margin:5px">My To Do List</h2>
    <input type="text" v-model="newTodo" id="myInput" placeholder="Title...">
    <span class="addBtn" @click="addNewTodo">Add</span>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodo: ''
    }
  },

  methods: {
    addNewTodo() {
      if (this.newTodo.trim() !== '') {
        this.$emit('add-todo', this.newTodo);
        this.newTodo = '';
      }
    }
  }
}
</script>