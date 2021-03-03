<template>
  <div class="nav">
    <!-- <h1>PROJECT-PLANNER</h1> -->
    <router-link to="/">Projects</router-link>
    <router-link to="/add">Add a Project</router-link>
  </div>
</template>

<script>
export default {};
</script>

<style>
/* .nav { */
/* display: flex; */
/* flex-direction: row; */
/* justify-content: space-evenly; */
/* } */
.nav {
  /* padding: 30px; */
  padding-top: 1rem;
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
}
.nav a {
  font-weight: bold;
  font-size: 1.75rem;
  /* color: #2c3e50; */
  color: #1d2935;
  text-decoration: none;
}
.nav a.router-link-exact-active {
  /* color: #2f4d3f; */
  /* color: rgb(12, 56, 41) 1px; */
  padding-bottom: 1rem;
  /* text-decoration-line: underline; */
  border-bottom: 0.3rem solid rgb(15, 172, 132);
}
</style>