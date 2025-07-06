<template>
  <div id="app">
    <Navbar />
    <main class="container">
      <router-view />
    </main>
  </div>
</template>

<script>
import Navbar from './components/NavBar.vue'

export default {
  name: 'AppRoot',
  components: {
    Navbar
  }
}
</script>

<style>
/* Global Reset & Base */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background-color: #f4f7fb;
  color: #2c3e50;
  line-height: 1.6;
}

/* App Container */
#app {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  background: linear-gradient(to bottom, #f4f7fb 0%, #e0ecff 100%);
}

/* Main Content */
.container {
  flex: 1;
  padding: 30px 20px;
  max-width: 1200px;
  margin: 0 auto;
  animation: fadeIn 0.5s ease-in-out;
}

/* Page Fade Animation */
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(12px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Scrollbar Styling (Optional for aesthetic touch) */
::-webkit-scrollbar {
  width: 10px;
}
::-webkit-scrollbar-track {
  background: #f0f2f5;
}
::-webkit-scrollbar-thumb {
  background: #b0c4de;
  border-radius: 6px;
}
::-webkit-scrollbar-thumb:hover {
  background: #4a90e2;
}
</style>
