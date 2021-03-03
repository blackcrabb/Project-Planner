<template>
  <h1>Project Planner</h1>
  <Navbar />
  <router-view />
</template>

<script>
import Navbar from "./components/Navbar";
export default {
  components: { Navbar },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  /* color: #2c3e50; */
  color: #1d2935;
}
h1 {
  font-size: 3rem;
  /* background: white; */
  /* height: 8vh; */
  /* opacity: 0.8; */
}
</style>
