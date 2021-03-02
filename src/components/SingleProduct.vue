<template>
  <div class="icon">
    <p>{{ project.title }}</p>
    <span @click="deleteProject" class="material-icons">delete</span>
    <span class="material-icons">edit</span>
    <span class="material-icons tick">done</span>
  </div>
  <br />
</template>

<script>
export default {
  props: ["project"],
  data() {
    return {
      uri: "http://localhost:3000/projects/" + this.project.id,
    };
  },
  methods: {
    deleteProject() {
      fetch(this.uri, { method: "DELETE" })
        .then(() => this.$emit("delete", this.project.id))
        .catch((err) => console.log(err));
    },
  },
};
</script>

<style>
p {
  font-size: 1.7rem;
}
.icon {
  padding-left: 0.5rem;
  border: solid black 0.08rem;
  /* padding-left: 25rem; */
  border-radius: 10px;
  width: 40vw;
  display: flex;
  flex-direction: row;
  /* justify-content: left; */
  /* padding-bottom: 5px; */
}
.material-icons {
  font-size: 2.5rem;
  padding-top: 1.2rem;
  padding-left: 2rem;
  /* margin-left: 10px; */
  color: #2c3e50;
  cursor: pointer;
  float: right;
}
</style>