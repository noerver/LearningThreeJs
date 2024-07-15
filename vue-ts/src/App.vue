<script setup lang="ts">
import Demo1 from './components/Demo1.vue'
</script>

<template>
  <div>
    <h1>Wellcome to learning three.js</h1>
  </div>
  <Demo1 msg="Vite + Vue" />
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
