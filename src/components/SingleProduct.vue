<template>
  <div class="icon">
    <p @click="showDetails = !showDetails">{{ project.title }}</p>
    <span @click="deleteProject" class="material-icons">delete</span>
    <router-link :to="{ name: 'EditProject', params: { id: project.id } }">
      <span class="material-icons">edit</span>
    </router-link>
    <span @click="toggleComplete" class="material-icons tick">done</span>
  </div>
  <br />
  <div v-if="showDetails" class="details">
    {{ project.description }}
  </div>
  <!-- <br /> -->
</template>

<script>
export default {
  props: ["project"],
  data() {
    return {
      uri: "http://localhost:3000/projects/" + this.project.id,
      showDetails: false,
    };
  },
  methods: {
    deleteProject() {
      fetch(this.uri, { method: "DELETE" })
        .then(() => this.$emit("delete", this.project.id))
        .catch((err) => console.log(err));
    },
    toggleComplete() {
      fetch(this.uri, {
        method: "PATCH",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({ completed: !this.project.completed }),
      })
        .then(() => {
          this.$emit("completed", this.project.id);
        })
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
  /* border: solid black 0.08rem; */
  border-left: solid #2c3e50 1rem;
  /* padding-left: 25rem; */
  border-radius: 10px;
  width: 40vw;
  display: flex;
  flex-direction: row;
  background-color: white;
  opacity: 0.8;
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

.details {
  padding-top: 0.4rem;
  width: 42vw;
  font-size: 1.2rem;
  background: white;
  opacity: 0.8;
  border-radius: 10px;
}
</style>