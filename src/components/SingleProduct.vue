<template>
  <div v-for="project in projects">
    <span>
      <p>{{ project.title }}</p>
      {{ project.description }}
    </span>
    <br />
  </div>
</template>

<script>
export default {
  props: ["projects"],
};
</script>

<style>
</style>