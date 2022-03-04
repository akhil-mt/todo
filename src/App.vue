<template>
  <div>
    <todo-list>
    </todo-list>
  </div>
</template>

<script>
import todoList from './components/todoList.vue'
import './assets/tailwind.css'

export default {
  name: 'App',
  components: {
    todoList
  }
}
</script>

<style>

</style>
