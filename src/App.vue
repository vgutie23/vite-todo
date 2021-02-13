<!--Vanessa Gutierrez 02/12/2021-->
<template>
  <div class="min-h-screen flex flex-col justify-center items-center">
    <Header />
    <Main>
      <ListTodos color="pink" title="Incomplete Items" :todos="pendingTodos" />
      <ListTodos
        color="yellow"
        title="Completed Items"
        :todos="completedTodos"
      />
    </Main>
  </div>
</template>

<script setup>
import Header from './components/Header.vue'
import Main from './components/Main.vue'
import ListTodos from './components/ListTodos.vue'
import { pendingTodos, completedTodos } from './helpers/useTodos'
</script>
