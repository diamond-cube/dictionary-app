<template>
  <div class="background p-5">
    <h1>Dictionary App</h1>
  </div>
  <br />
  <Dictionary />
</template>

<script setup>
import Dictionary from "./components/Dictionary.vue";
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: left;
  justify-content: left; */
  color: #2c3e50;
}

.background {
  background-color: rgb(95, 172, 235);
  color: white;
  /* text-align: left; */
}
</style>
