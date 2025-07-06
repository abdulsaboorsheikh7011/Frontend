<template>
  <div class="albums-container">
    <h2 class="heading">📀 Albums</h2>
    <div v-if="loading" class="loading">Loading albums...</div>
    <div v-else class="album-grid">
      <div v-for="album in albums" :key="album.id" class="card">
        <h4 class="title">{{ album.title }}</h4>
        <p class="info">Album ID: {{ album.id }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'AlbumsPage',
  data() {
    return {
      albums: [],
      loading: true
    }
  },
  mounted() {
    axios.get('https://jsonplaceholder.typicode.com/albums')
      .then(res => {
        this.albums = res.data
        this.loading = false
      })
  }
}
</script>

<style scoped>
.albums-container {
  max-width: 1000px;
  margin: 40px auto;
  padding: 0 20px;
  font-family: 'Segoe UI', sans-serif;
}

.heading {
  text-align: center;
  font-size: 2rem;
  color: #333;
  margin-bottom: 30px;
}

.loading {
  text-align: center;
  font-size: 1.2rem;
  color: #555;
}

.album-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
  gap: 20px;
}

.card {
  background: #ffffff;
  border: 1px solid #d1ecf1;
  border-left: 5px solid #00bcd4;
  border-radius: 10px;
  padding: 20px;
  transition: transform 0.2s ease, box-shadow 0.3s ease;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.05);
}

.card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
}

.title {
  font-size: 1.1rem;
  color: #007b8a;
  margin-bottom: 8px;
}

.info {
  color: #555;
  font-size: 0.95rem;
}
</style>
