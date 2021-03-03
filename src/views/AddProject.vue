<template>
  <form @submit.prevent="handleSubmit">
    <label> Title</label>
    <input type="text" v-model="title" required />
    <br />
    <label> Details</label>
    <textarea v-model="description" required></textarea>
    <button type="submit">SUBMIT</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      title: "",
      description: "",
    };
  },
  methods: {
    handleSubmit() {
      let project = {
        title: this.title,
        description: this.description,
        completed: false,
        id: Math.floor(Math.random() * 100),
      };
      fetch("http://localhost:3000/projects", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(project),
      })
        .then(() => {
          this.$router.push("/");
        })
        .catch((err) => console.log(err));
    },
  },
};
</script>

<style>
form {
  padding: 1rem;
  border-radius: 10px;
}
label {
  display: block;
  color: #1d2935;
  text-transform: uppercase;
  font-size: 1.2rem;
  font-weight: bold;
  letter-spacing: 1px;
  margin: 20px 0 10px 0;
}
input {
  padding: 10px;
  border: 0;
  border-bottom: 1px solid #ddd;
  width: 50%;
  box-sizing: border-box;
}
textarea {
  border: 1px solid #ddd;
  padding: 10px;
  width: 50%;
  box-sizing: border-box;
  height: 100px;
}
form button {
  display: block;
  margin: 20px auto 0;
  background: #00ce89;
  color: white;
  padding: 10px;
  border: 0;
  border-radius: 6px;
  font-size: 16px;
}
</style>