<template>
  <FilterNav />
  <div v-if="error">{{ error }}</div>
  <div class="projectlist" v-for="project in projects">
    <span>
      <p>{{ project.title }}</p>
      {{ project.description }}</span
    >
    <br />
  </div>
</template>

<script>
import { ref } from "vue";
// @ is an alias to /src
import FilterNav from "../components/FilterNav";

export default {
  name: "Home",
  components: {
    FilterNav,
  },
  setup() {
    const projects = ref([]);
    const error = ref(null);

    const load = async () => {
      try {
        let data = await fetch("http://localhost:3000/projects");
        if (!data.ok) {
          throw Error("no data available");
        }
        projects.value = await data.json();
      } catch (err) {
        error.value = err.message;
      }
    };

    load();

    return { projects, error };
  },
};
</script>
<style>
p {
  font-size: 1.7rem;
}
span {
  border: solid black 0.08rem;
  /* padding-left: 25rem; */
  border-radius: 10px;
  width: 50vw;
  display: flex;
  flex-direction: column;
  /* justify-content: left; */
  padding-bottom: 5px;
}
.projectlist {
  padding-left: 25rem;
}
</style>
