<template>
  <div id="app">
    <Navbar />
    <main class="container">
      <router-view />
    </main>
  </div>
</template>

<script>
import Navbar from './components/NavBar.vue';

export default {
  name: 'AppRoot',
  components: {
    Navbar
  }
}
</script>

<style>
body {
  margin: 0;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background-color: #f0f2f5;
}

.container {
  padding: 20px;
}
</style>