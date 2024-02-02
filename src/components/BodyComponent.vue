<!-- BodyComponent.vue -->
<template>
  <ul id="myUL">
    <li v-for="todo in todoList" :key="todo.no" @click="toggleTodoStatus(todo)">
      <span :class="{ checked: todo.cancelFlag }">{{ todo.todo }}</span>
      <span class="close" @click.stop="deleteTodoItem(todo.no)">X</span>
    </li>
  </ul>
</template>

<script>
export default {
  props: ['todoList'],
  methods: {
    deleteTodoItem(todoNo) {
      this.$emit('delete-todo', todoNo);
    },
    toggleTodoStatus(todo) {
      todo.cancelFlag = !todo.cancelFlag;
    }
  }
}
</script>

<style scoped>
/* Style the list items */
ul li {
  cursor: pointer;
  position: relative;
  padding: 12px 8px 12px 40px;
  list-style-type: none;
  background: #eee;
  font-size: 18px;
  transition: 0.2s;
}

/* Set all odd list items to a different color (zebra-stripes) */
ul li:nth-child(odd) {
  background: #f9f9f9;
}

/* Darker background-color on hover */
ul li:hover {
  background: #ddd;
}

/* Style the checked item */
ul li .checked {
  text-decoration: line-through;
}

/* Style the close button */
.close {
  position: absolute;
  right: 0;
  top: 0;
  padding: 12px 16px 12px 16px;
}

.close:hover {
  background-color: #f44336;
  color: white;
}
</style>