<template>
  <div>
    <h1>{{ msg }}</h1>

    <form @submit.prevent="addTodo">
      <input type="text" v-model="newTodo" placeholder="Enter a task" />
      <button type="submit">Add</button>
    </form>

    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        {{ todo }}
        <button @click="removeTodo(index)">Remove</button>
      </li>
    </ul>
    
  </div>
</template>

<script setup>
import { ref } from 'vue'

defineProps({
  msg: String,
})

const count = ref(0)
const todos = ref([])
const newTodo = ref('')

const addTodo = () => {
  if (newTodo.value.trim() !== '') {
    todos.value.push(newTodo.value)
    newTodo.value = ''
  }
}

const removeTodo = (index) => {
  todos.value.splice(index, 1)
}
</script>
