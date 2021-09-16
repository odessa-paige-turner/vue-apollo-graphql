<template>
  <div id="app">
    <Launches />
  </div>
</template>

<script>
// import Users from "./components/Users";
import Launches from "./components/Launches";

export default {
  name: 'App',
  components: {
    // Launches
    Launches
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
