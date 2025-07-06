<template>
  <div class="comments-container">
    <h2 class="heading">💬 Comments</h2>
    <div v-if="loading" class="loading">Fetching comments...</div>
    <div v-else class="comment-list">
      <div v-for="comment in comments" :key="comment.id" class="card">
        <h4 class="comment-name">{{ comment.name }}</h4>
        <p class="email"><strong>📧 Email:</strong> {{ comment.email }}</p>
        <p class="body">{{ comment.body }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'CommentsPage',
  data() {
    return {
      comments: [],
      loading: true
    }
  },
  mounted() {
    axios.get('https://jsonplaceholder.typicode.com/comments')
      .then(res => {
        this.comments = res.data
        this.loading = false
      })
  }
}
</script>

<style scoped>
.comments-container {
  max-width: 1100px;
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

.comment-list {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 20px;
}

.card {
  background: #fff9f0;
  border: 1px solid #ffdab9;
  border-left: 6px solid #ff7f50;
  border-radius: 10px;
  padding: 20px;
  transition: transform 0.2s ease, box-shadow 0.3s ease;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.05);
}

.card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 18px rgba(0, 0, 0, 0.1);
}

.comment-name {
  font-size: 1.1rem;
  color: #cc3300;
  margin-bottom: 8px;
}

.email {
  color: #444;
  font-size: 0.95rem;
  margin-bottom: 6px;
}

.body {
  font-size: 0.95rem;
  color: #333;
  line-height: 1.4;
}
</style>
