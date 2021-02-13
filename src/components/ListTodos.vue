<!--Vanessa Gutierrez 02/12/2021-->
<template>
  <section class="space-y-4" v-if="todos.length > 0">
    <h3
      class="text-3xl font-normal"
      :class="color === 'pink' ? 'text-pink-500' : 'text-yellow-500'"
    >
      {{ title }}: {{ todos.length }}
    </h3>
    <ul class="space-y-4">
      <li
        v-for="todo in todos"
        :key="todo.id"
        class="bg-white rounded-xl text-2xl py-2 px-4 font-normal text-center hover:text-white cursor-pointer transition-colors"
        :class="
          color === 'pink'
            ? 'text-pink-500 hover:bg-pink-500'
            : 'text-yellow-500 hover:bg-yellow-500'
        "
        @click="changeStatus(todo.id)"
      >
        {{ todo.text }}
      </li>
    </ul>
  </section>
</template>

<script setup>
import { defineProps } from 'vue'
import { changeStatus } from '../helpers/useTodos'

defineProps({
  color: {
    type: String,
    default: 'pink',
  },
  title: {
    type: String,
    default: 'Todo List',
  },
  todos: {
    type: Array,
    default: [],
  },
})
</script>
