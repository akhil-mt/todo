<template>
  <div>
    <section>
      <h1 class="text-2xl uppercase font-black mb-6 text-center mt-6">
        {{ title }}
      </h1>
      <div
        class="flex justify-center border w-1/3 m-auto p-2 rounded-full border-blue-800"
      >
        <input
          v-model="newTodo"
          name=""
          id=""
          cols="60"
          rows="1"
          placeholder="Enter your task"
          class="border-none p-2 rounded-lg resize-none focus:outline-none flex-1"
        />

        <button
          @click.prevent="addTodo"
          class="rounded-full border px-8 py-2 bg-blue-800 text-white"
        >
          Submit
        </button>
      </div>
      <div class="w-1/3 m-auto p-4 uppercase text-sm font-semibold border-b">
        <p>Your To-Do</p>
      </div>

      <div class="w-1/3 m-auto">
        <div v-for="todo in todos" v-bind:key="todo">
          <div class="border-b flex justify-between items-center">
            <div class="p-4 inline-block">
              <!-- <input :name="todo.title" type="checkbox" v-model="todo.done" /> -->
              <div class="text-sm break-all">{{ todo.title }}</div>
            </div>

            <button
              style="min-width: 40px"
              @click="removeTodo(todo)"
              type="button"
              name="button"
              class="rounded-full bg-red-500 hover:bg-red-900 text-white p-2 w-10 h-10 min-w-10"
            >
              X
            </button>
          </div>
        </div>
      </div>
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
  created() {
    const storagestring = localStorage.getItem("todostore");
    if (storagestring) {
      const saved = JSON.parse(storagestring);
      this.todos = saved;
    }
  },
  methods: {
    addTodo() {
      this.todos.push({
        title: this.newTodo,
        done: false,
      });
      this.newTodo = "";
      const _todo = JSON.stringify(this.todos);
      console.log(this.todos);
      console.log(_todo);
      localStorage.setItem("todostore", _todo);
    },
    removeTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos.splice(todoIndex, 1);
      const _todo = JSON.stringify(this.todos);
      
      localStorage.setItem("todostore", _todo);

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
