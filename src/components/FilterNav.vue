<template>
  <div class="filnav">
    <button><h5>VIEW ALL</h5></button>
    <button><h5>COMPLETED</h5></button>
    <button><h5>ONGOING</h5></button>
  </div>
  <br />
</template>

<script>
export default {};
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
}
.filnav button {
  padding: 0;
  background: none;
  border-bottom: 0.3rem solid rgb(255, 255, 255);
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