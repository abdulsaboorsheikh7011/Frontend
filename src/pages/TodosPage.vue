<template>
  <div class="todos-container">
    <h2 class="heading">✅ Todo List</h2>
    <div v-if="loading" class="loading">Loading todos...</div>
    <div v-else>
      <div v-for="todo in todos" :key="todo.id" class="card" :class="{ done: todo.completed, pending: !todo.completed }">
        <p class="todo-title">{{ todo.title }}</p>
        <p class="status">
          Status:
          <strong :class="todo.completed ? 'text-success' : 'text-danger'">
            {{ todo.completed ? 'Done' : 'Pending' }}
          </strong>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'TodosPage',
  data() {
    return {
      todos: [],
      loading: true
    }
  },
  mounted() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=30')
      .then(res => {
        this.todos = res.data
        this.loading = false
      })
  }
}
</script>

<style scoped>
.todos-container {
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
  background: #fff8e1;
  border-left: 6px solid #ffc107;
  border-radius: 10px;
  padding: 16px;
  margin-bottom: 15px;
  transition: all 0.2s ease;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.05);
}

.card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
}

.todo-title {
  font-size: 1.05rem;
  font-weight: 500;
  color: #444;
  margin-bottom: 8px;
}

.status {
  font-size: 0.95rem;
}

.text-success {
  color: #2e7d32;
}

.text-danger {
  color: #c62828;
}

.done {
  border-left-color: #28a745;
  background: #e8f5e9;
}

.pending {
  border-left-color: #f44336;
  background: #fff3f3;
}
</style>
