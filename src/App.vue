<!--Vanessa Gutierrez 02/06/2021-->
<template>
  <div class="min-h-screen flex flex-col justify-center items-center">
    <header class="flex flex-col w-full container">
      <h1 class="text-6xl font-semibold text-pink-500 text-center">
        💖 My To Do List 💖
      </h1>
      <input
        class="text-3xl py-2 px-4 rounded-xl w-full mt-8 text-gray-600"
        type="text"
        placeholder="New List Item"
        v-model="newTodo"
        @change="addTodo"
      />
    </header>
    <main class="container w-full mt-8 space-y-8">
      <section class="space-y-4" v-if="pendingTodos.length > 0">
        <h3 class="text-3xl font-normal text-pink-500">
          Incomplete Items: {{ pendingTodos.length }}
        </h3>
        <ul class="space-y-4">
          <li
            v-for="todo in pendingTodos"
            :key="todo.id"
            class="bg-white rounded-xl text-2xl py-2 px-4 font-normal text-pink-500 text-center hover:text-white hover:bg-pink-500 cursor-pointer transition-colors"
            @click="changeStatus(todo.id)"
          >
            {{ todo.text }}
          </li>
        </ul>
      </section>
      <section class="space-y-4" v-if="completedTodos.length > 0">
        <h3 class="text-3xl font-normal text-yellow-500">
          Completed Items: {{ completedTodos.length }}
        </h3>
        <ul class="space-y-4">
          <li
            v-for="todo in completedTodos"
            :key="todo.id"
            class="bg-white rounded-xl text-2xl py-2 px-4 font-normal text-yellow-500 text-center hover:text-white hover:bg-yellow-500 cursor-pointer transition-colors"
            @click="changeStatus(todo.id)"
          >
            {{ todo.text }}
          </li>
        </ul>
      </section>
    </main>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const newTodo = ref('')

const todos = ref([])

const pendingTodos = computed(() =>
  todos.value.filter(todo => todo.status === 'pending'),
)

const completedTodos = computed(() =>
  todos.value.filter(todo => todo.status === 'done'),
)

const changeStatus = id => {
  todos.value.map(todo => {
    if (todo.id === id) {
      todo.status = todo.status === 'pending' ? 'done' : 'pending'
    }
  })
}

const addTodo = () => {
  if (newTodo.value.length > 0) {
    todos.value.push({
      id: todos.value.length,
      text: newTodo.value,
      status: 'pending',
    })
    newTodo.value = ''
  }
}
</script>
