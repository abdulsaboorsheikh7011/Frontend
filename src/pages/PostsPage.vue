<template>
  <div class="posts-container">
    <h2 class="heading">📝 Posts</h2>
    <div v-if="loading" class="loading">Loading posts...</div>
    <div v-else>
      <div v-for="post in posts" :key="post.id" class="card">
        <div class="post-id">#{{ post.id }}</div>
        <h3 class="post-title">{{ post.title }}</h3>
        <p class="post-body">{{ post.body }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'PostsPage',
  data() {
    return {
      posts: [],
      loading: true
    }
  },
  mounted() {
    axios.get('https://jsonplaceholder.typicode.com/posts')
      .then(res => {
        this.posts = res.data
        this.loading = false
      })
  }
}
</script>

<style scoped>
.posts-container {
  max-width: 900px;
  margin: 40px auto;
  padding: 0 20px;
  font-family: 'Segoe UI', sans-serif;
}

.heading {
  text-align: center;
  font-size: 2rem;
  color: #2c3e50;
  margin-bottom: 30px;
}

.loading {
  text-align: center;
  font-size: 1.2rem;
  color: #555;
}

.card {
  background: #ffffff;
  border-left: 5px solid #4a90e2;
  border-radius: 10px;
  padding: 20px;
  margin-bottom: 16px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
  transition: transform 0.2s ease, box-shadow 0.3s ease;
}

.card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.1);
}

.post-id {
  font-size: 0.9rem;
  color: #888;
  margin-bottom: 4px;
}

.post-title {
  font-size: 1.2rem;
  color: #34495e;
  margin-bottom: 8px;
  font-weight: 600;
}

.post-body {
  font-size: 1rem;
  color: #444;
  line-height: 1.5;
}
</style>
