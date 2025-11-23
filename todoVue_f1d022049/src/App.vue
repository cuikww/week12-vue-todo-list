<script setup>
import { ref } from 'vue'

const newTask = ref('')
const tasks = ref([])


const addTask = () => {
  if (newTask.value.trim() !== '') {
    tasks.value.push(newTask.value)
    newTask.value = ''
  }
}


const removeTask = (index) => {
  tasks.value.splice(index, 1)
}
</script>

<template>
  <div class="container">
    <h1>Daftar Tugas Vue</h1>

    <form @submit.prevent="addTask" class="input-group">
      <input 
        v-model="newTask" 
        placeholder="Tambahkan tugas baru..." 
        type="text"
      />
      <button type="submit">Tambah</button>
    </form>

    <p v-if="tasks.length === 0" class="empty-msg">
      Tidak ada tugas. Silakan tambahkan tugas baru.
    </p>

    <ul v-else>
      <li v-for="(task, index) in tasks" :key="index">
        <span>{{ task }}</span>
        <button @click="removeTask(index)" class="delete-btn">Hapus</button>
      </li>
    </ul>
  </div>
</template>

<style scoped>

.container {
  max-width: 400px;
  margin: 50px auto;
  padding: 20px;
  font-family: Arial, sans-serif;
  border: 1px solid #ddd;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
}

h1 {
  text-align: center;
  color: #42b983;
}

.input-group {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}

input {
  flex: 1;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

button {
  cursor: pointer;
  padding: 8px 12px;
  border: none;
  border-radius: 4px;
  background-color: #42b983;
  color: white;
}

button:hover {
  background-color: #3aa876;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  background: #f9f9f9;
  margin-bottom: 8px;
  padding: 10px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-radius: 4px;
}

.delete-btn {
  background-color: #ff4d4d;
  font-size: 0.8rem;
}

.delete-btn:hover {
  background-color: #e60000;
}

.empty-msg {
  text-align: center;
  color: #888;
  font-style: italic;
}
</style>