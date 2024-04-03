<template>
  <div class="todo-app">
    <div class="task-input">
      <input type="text" v-model="newTask" @keyup.enter="addTask" placeholder="add task" />
      <button @click="addTask">add to-do</button>
    </div>

    <!-- RENDERING ALL TASKS -->

    <ul class="task-list">
      <li v-for="(task, index) in tasks" :key="index" class="task-item">
        <input
          v-if="editIndex === index"
          type="text"
          v-model="task.title"
          @keyup.enter="updateTask(index)"
          class="editing"
        />
        <span v-else>{{ task.title }}</span>
        <button @click="editTask(index)" class="edit-button">Edit</button>
        <button @click="removeTask(index)" class="remove-button">Remove</button>
      </li>
    </ul>
    <button @click="clear" class="clear">clear</button>
  </div>
</template>

<script setup>
import { ref } from 'vue'

// REACTIVE REFERENCES FOR NEW TASK INPUT, TASKS ARRAY, AND TASK BEING EDITED
const newTask = ref('')
const tasks = ref([])
const editIndex = ref(null)

// ADD TASK FUNCTION
const addTask = () => {
  if (newTask.value.trim() != '') {
    tasks.value.push({ title: newTask.value })
    newTask.value = ''
  }
}

// TARGET TASKS
const editTask = (index) => {
  editIndex.value = index
}

// UPDATE TASK FUNCTION
const updateTask = (index) => {
  tasks.value[index] = { title: tasks.value[index].title }
  editIndex.value = null
}

//REMOVE TASK FUNCTION
const removeTask = (index) => {
  tasks.value.splice(index, 1)
}

// CLEAR TASKS FUNCTION
const clear = () => {
  tasks.value = []
}
</script>

<style scoped>
.todo-app {
  max-width: 600px;
  margin: 50px auto;
  padding: 30px;
  border: 1px solid #ddd;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  background-color: #f8f9fa;
}

.task-input {
  display: flex;
  gap: 15px;
}

input {
  flex: 1;
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ddd;
  border-radius: 5px;
}

button {
  padding: 10px 15px;
  font-size: 16px;
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #0056b3;
}

.task-list {
  list-style: none;
  padding: 0;
}

.task-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px;
  margin: 10px 0;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 5px;
}

.remove-button {
  padding: 8px 12px;
  font-size: 14px;
  background-color: #dc3545;
  color: #fff;
  border: none;
  border-radius: 3px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.remove-button:hover {
  background-color: #c82333;
}

.edit-button {
  padding: 8px 12px;
  font-size: 14px;
  background-color: #ffc107;
  color: #fff;
  border: none;
  border-radius: 3px;
  cursor: pointer;
  transition: background-color 0.3s ease;
  margin-left: 10px;
}

.edit-button:hover {
  background-color: #e0a800;
}

input[type='text'].editing {
  border: 2px solid #ffc107;
}

.clear {
  display: block;
  width: 100%;
  padding: 10px;
  margin-top: 20px;
  font-size: 16px;
  text-align: center;
  background-color: #28a745;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.clear:hover {
  background-color: #218838;
}
</style>
