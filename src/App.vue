<script setup>
import Index from './components/TabView.vue'
import './assets/main.css'
</script>

<template>
  <div class="app">
    <Index />
  </div>
</template>

<style>
.app {
  width: 100%;
  height: 100vh;
  background-color: #000000;
  color: #ffffff;
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  display: flex;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background-color: #000000;
  margin: 0;
  padding: 0;
  line-height: 1.5;
}

@media (max-width: 768px) {
  .app {
    flex-direction: column;
  }
}
</style>
