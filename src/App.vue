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
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
