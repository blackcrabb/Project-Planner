<template>
  <div class="filnav">
    <button @click="updateFilter('all')" :class="{ active: current === 'all' }">
      <h5>VIEW ALL</h5>
    </button>
    <button
      @click="updateFilter('completed')"
      :class="{ active: current === 'completed' }"
    >
      <h5>COMPLETED</h5>
    </button>
    <button
      @click="updateFilter('ongoing')"
      :class="{ active: current === 'ongoing' }"
    >
      <h5>ONGOING</h5>
    </button>
  </div>
  <br />
</template>

<script>
export default {
  props: ["current"],
  methods: {
    updateFilter(by) {
      this.$emit("filterChange", by);
    },
  },
};
</script>

<style>
.filnav {
  padding-top: 1.4rem;
  display: flex;
  flex-direction: row;
  justify-content: center;
}

.filnav h5 {
  padding-right: 1.4rem;
  font-size: 1.25rem;
  color: #1d2935;
}
.filnav button {
  padding: 0;
  background: none;
  border-bottom: 0.3rem solid #6467aa;
  border-top: none;
  border-left: none;
  border-right: none;
  outline: none;
}
.filnav button:active {
  border-bottom: 0.3rem solid rgb(15, 172, 132);
  border-top: none;
  border-left: none;
  border-right: none;
  outline: none;
}
</style>