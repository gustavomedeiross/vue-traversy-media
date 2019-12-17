<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Todos from "./components/Todos";
import Header from "./components/Header";
import AddTodo from "./components/AddTodo";

import api from "./services/api";

export default {
  name: "app",
  components: {
    Todos,
    Header,
    AddTodo
  },
  data() {
    return {
      todos: []
    };
  },
  methods: {
    async deleteTodo(id) {
      await api.delete(`todos/${id}`);
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    async addTodo(newTodo) {
      const { title, completed } = newTodo;

      const response = await api.post("todos", {
        title,
        completed
      });

      this.todos = [...this.todos, response.data];
    }
  },
  async created() {
    const response = await api.get("todos?_limit=5");
    this.todos = response.data;
  }
};
</script>

<style>
*,
*::before,
*::after {
  padding: 0;
  margin: 0;
  outline: 0;
  border: 0;
  box-sizing: border-box;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}

button {
  cursor: pointer;
}

.btn {
  display: inline-block;
  background: #555;
  color: #fff;
  padding: 7px 20px;
}

.btn:hover {
  background: #666;
}
</style>
