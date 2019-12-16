<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import axios from "axios";
import Todos from "./components/Todos";
import Header from "./components/Header";
import AddTodo from "./components/AddTodo";

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
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(newTodo) {
      this.todos = [...this.todos, newTodo];
    },
    created() {
      axios.get("");
    }
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
