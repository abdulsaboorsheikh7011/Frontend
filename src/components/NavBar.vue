<template>
  <nav class="navbar">
    <router-link to="/posts" class="nav-link">Posts</router-link>
    <router-link to="/comments" class="nav-link">Comments</router-link>
    <router-link to="/albums" class="nav-link">Albums</router-link>
    <router-link to="/photos" class="nav-link">Photos</router-link>
    <router-link to="/todos" class="nav-link">Todos</router-link>
    <router-link to="/users" class="nav-link">Users</router-link>
  </nav>
</template>

<script>
export default {
  name: 'NavBar'
}
</script>

<style scoped>
.navbar {
  background: linear-gradient(90deg, #d1fd0d, #f24810);
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 16px;
  padding: 18px 12px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
  border-radius: 12px;
  margin: 20px;
}

.nav-link {
  color: #fff;
  font-weight: 600;
  text-decoration: none;
  padding: 10px 18px;
  border-radius: 8px;
  transition: all 0.3s ease;
  background-color: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(3px);
}

.nav-link:hover {
  background-color: rgba(255, 255, 255, 0.393);
  transform: scale(1.05);
}

.router-link-exact-active {
  background-color: rgba(255, 255, 255, 0.3);
  border: 2px solid #ffffff;
}
</style>
