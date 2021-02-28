<template>
  <FilterNav />
  <div v-for="project in projects">
    <span>
      {{ project.title }} <br />
      {{ project.description }}</span
    >
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

    return { posts };
  },
};
</script>

