<template>
  <div class="photos-container">
    <h2 class="heading">📷 Photo Gallery</h2>
    <div v-if="loading" class="loading">Loading photos...</div>
    <div v-else class="grid">
      <div v-for="photo in photos" :key="photo.id" class="card">
        <img :src="photo.thumbnailUrl" :alt="photo.title" />
        <p class="caption">{{ photo.title }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'PhotosPage',
  data() {
    return {
      photos: [],
      loading: true
    }
  },
  mounted() {
    axios.get('https://jsonplaceholder.typicode.com/photos?_limit=30')
      .then(res => {
        this.photos = res.data
        this.loading = false
      })
  }
}
</script>

<style scoped>
.photos-container {
  max-width: 1200px;
  margin: 40px auto;
  padding: 0 20px;
  font-family: 'Segoe UI', sans-serif;
}

.heading {
  text-align: center;
  font-size: 2.2rem;
  color: #2c3e50;
  margin-bottom: 30px;
}

.loading {
  text-align: center;
  font-size: 1.2rem;
  color: #555;
}

.grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
  gap: 20px;
}

.card {
  background: #fefefe;
  border-radius: 12px;
  overflow: hidden;
  padding: 10px;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.05);
  text-align: center;
  border: 1px solid #ddd;
}

.card:hover {
  transform: translateY(-6px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
  border-color: #00bcd4;
}

img {
  width: 100%;
  height: auto;
  border-radius: 8px;
  margin-bottom: 10px;
}

.caption {
  font-size: 0.95rem;
  color: #34495e;
  font-weight: 500;
  padding: 0 5px;
  word-break: break-word;
}
</style>
