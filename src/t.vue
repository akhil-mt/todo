<template>
  <div>
    <section>
      <h1 class="text-4xl">{{ title }}</h1>
      <textarea
        v-model="newTodo"
        name=""
        id=""
        cols="60"
        rows="5"
        placeholder="Enter your task"
      ></textarea
      ><br />
      <!-- <input v-model="newTodo" type="textarea" placeholder="Enter your task" name="newTodo" id="newTodo" ><br> -->
      <button @click.prevent="addTodo">Submit</button>
      <p>{{ newTodo }}</p>

      <ul>
        <li v-for="todo in todos" v-bind:key="todo">
          <input type="checkbox" v-model="todo.done" />
          <p>{{todo.title}}</p><br>
          <button @click="removeTodo(todo)" type="button" name="button"><br>
            Remove
          </button>
        </li>
      </ul>
    </section>
  </div>
</template>

<script>
export default {
  name: "todoList",
  // props: {
  //   msg: String
  data() {
    return {
      title: "To-Do-List",
      newTodo: "",
      todos: [],
    };
  },
  methods: {
    addTodo() {
      this.todos.push({
        title: this.newTodo,
        done: false,
      });
      this.newTodo = "";
    },
    removeTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos.splice(todoIndex, 1);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

