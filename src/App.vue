<template>
  <div class="flex justify-center min-h-[100vh] items-center flex-col">
    <AddTodo @add-todo="handleAddTodo" />
    <TodoList :todos="todos" @delete-todo="handleDeleteTodo" @complete-todo="handleCompleteTodo" />
  </div>
</template>

<script setup>
import AddTodo from './components/AddTodo.vue'
import TodoList from './components/TodoList.vue'
import { ref } from 'vue'

const todos = ref([])

const handleAddTodo = (todo) => {
  console.log('handleAddTodo', todo)
  todos.value.push(todo)
}

const handleDeleteTodo = (todoId) => {
  console.log('handleDeleteTodo')
  todos.value = todos.value.filter((todo) => todo.id !== todoId)
}

const handleCompleteTodo = (todoId) => {
  console.log('handleCompleteTodo')
  todos.value = todos.value.map((todo) =>
    todo.id === todoId ? { ...todo, complete: !todo.complete } : todo,
  )
}
</script>

<style></style>
