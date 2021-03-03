<template>
  <FilterNav :current="current" @filterChange="current = $event" />
  <div v-if="error">{{ error }}</div>
  <div class="projectlist">
    <div v-for="project in filteredProjects" :key="project.id">
      <SingleProduct :project="project" />
      <!-- <span> -->
      <!-- <p>{{ project.title }}</p> -->
      <!-- {{ project.description }} -->
      <!-- </span> -->
      <br />
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
// @ is an alias to /src
import FilterNav from "../components/FilterNav";
import SingleProduct from "../components/SingleProduct";

export default {
  name: "Home",
  components: {
    FilterNav,
    SingleProduct,
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
  data() {
    return {
      current: "all",
    };
  },
  computed: {
    filteredProjects() {
      if (this.current === "completed") {
        return this.projects.filter((project) => project.completed);
      }
      if (this.current === "ongoing") {
        return this.projects.filter((project) => !project.completed);
      }
      return this.projects;
    },
  },
};
</script>
<style>
.projectlist {
  padding-left: 25rem;
}
</style>
