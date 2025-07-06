<template>
  <div class="users-container">
    <h2 class="heading">👥 Users</h2>
    <div v-if="loading" class="loading">Loading user data...</div>
    <div v-else>
      <div v-for="user in users" :key="user.id" class="card">
        <h3 class="user-name">{{ user.name }}</h3>
        <p class="user-info"><strong>📧 Email:</strong> {{ user.email }}</p>
        <p class="user-info"><strong>📞 Phone:</strong> {{ user.phone }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'UsersPage',
  data() {
    return {
      users: [],
      loading: true
    }
  },
  mounted() {
    axios.get('https://jsonplaceholder.typicode.com/users')
      .then(res => {
        this.users = res.data
        this.loading = false
      })
  }
}
</script>

<style scoped>
.users-container {
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
  background: #f3f7ff;
  border-left: 5px solid #4a90e2;
  border-radius: 10px;
  padding: 18px;
  margin-bottom: 15px;
  transition: transform 0.2s ease, box-shadow 0.3s ease;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.05);
}

.card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 18px rgba(0, 0, 0, 0.1);
}

.user-name {
  color: #34495e;
  font-size: 1.3rem;
  margin-bottom: 8px;
  font-weight: 600;
}

.user-info {
  font-size: 0.95rem;
  color: #555;
  margin: 4px 0;
}
</style>
