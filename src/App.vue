<script setup>
import { ref } from "vue";

const name = ref("John Doe");
const status = ref("active");
const tasks = ref(["Task 1", "Task 2", "Task 3"]);

const newTask = ref("");

const toggleStatus = () => {
  if (status.value === "active") {
    status.value = "pending";
  } else if (status.value === "pending") {
    status.value = "active";
  } else {
    status.value = "active";
  }
};

function addTask() {
  if (newTask.value.trim() !== "") {
    tasks.value.push(newTask.value);
    newTask.value = "";
  }
}

function deleteTask(index) {
  tasks.value.splice(index, 1);
}
</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status === 'active'">User is active</p>
  <p v-else-if="status === 'pending'">User is pending</p>
  <p v-else="status">User is not active</p>

  <form @submit.prevent="addTask">
    <label for="newTask">Add Task</label>
    <input type="text" id="newTask" name="newTask" v-model="newTask" />
    <button type="submit">Submit</button>
  </form>

  <br />

  <h3>Tasks:</h3>
  <ul>
    <li v-for="(task, index) in tasks" :key="task">
      <span>{{ task }}</span>
      <button @click="deleteTask(index)">x</button>
    </li>
  </ul>

  <br />

  <!-- <button v-on:click="toggleStatus">Change status</button> -->
  <button @click="toggleStatus">Change status</button>
</template>
