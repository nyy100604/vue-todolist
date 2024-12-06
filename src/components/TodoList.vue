<template>
  <ul v-if="todos.length > 0">
    <li v-for="todo in todos" :key="todo.id" class="flex gap-3 my-2">
      <button class="bg-red-600 w-5 text-white" @click="deleteTodo(todo.id)">X</button>
      <button class="bg-green-600 w-5 text-white" @click="completeTodo(todo.id)">V</button>
      <p :class="{ 'line-through': todo.complete }">{{ todo.text }}</p>
    </li>
  </ul>
  <p v-else>No todos founds ...</p>
</template>

<script setup>
const emit = defineEmits(['deleteTodo', 'completeTodo'])

defineProps({
  todos: {
    type: Array,
  },
})

const deleteTodo = (todoId) => {
  emit('deleteTodo', todoId)
}

const completeTodo = (todoId) => {
  emit('completeTodo', todoId)
}
</script>

<style></style>
