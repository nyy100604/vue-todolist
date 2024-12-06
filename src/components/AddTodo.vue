<template>
  <form id="form" @submit.prevent="onSubmit">
    <div>
      <input
        type="text"
        placeholder="Todo Text..."
        class="border-gray-400 border-[2px] rounded-sm p-4 text-lg"
        v-model="text"
      />

      <div class="mt-2">
        <button class="bg-blue-500 text-white p-4 rounded-sm w-full">Add Todo</button>
      </div>
    </div>
  </form>
</template>

<script setup>
import { ref } from 'vue'

const text = ref('')

const emit = defineEmits(['addTodo'])

const onSubmit = () => {
  console.log('text', text.value)
  const todo = {
    id: crypto.randomUUID(),
    text: text.value,
    complete: false,
  }
  emit('addTodo', todo)
}
</script>

<style></style>
