<script>
import navbar from "./components/NavbarItem.vue";

export default {
  name: "App",
  components: {
    navbar,
  },
};
</script>

<template>
  <div id="app">
    <nav />
    <navbar />
  </div>
</template>

<style>
body {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  height: 100vh;
  width: 100vw;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
