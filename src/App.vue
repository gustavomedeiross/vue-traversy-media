<template>
  <div id="app">
    <Header />
    <router-view />
  </div>
</template>

<script>
import Header from "./components/Header";

export default {
  name: "app",
  components: {
    Header
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

a {
  text-decoration: none;
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
