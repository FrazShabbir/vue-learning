<script setup>
import { ref, onMounted } from "vue";

const name = ref("Fraz Shabbir");
const status = ref("active");
const tasks = ref(["Task 1", "Task 2", "Task 3"]);
const newTask = ref("");

const toggleStatus = () => {
  if (status.value === "active") {
    status.value = "pending";
  } else if (status.value === "pending") {
    status.value = "inactive";
  } else {
    status.value = "active";
  }
};

const addTask = () => {
  if (newTask.value !== "") {
    tasks.value.push(newTask.value);
    newTask.value = "";
  }
};

const deleteTask = (index) => {
  tasks.value.splice(index, 1);
};

onMounted(async () => {
  try {
    const response = await fetch("https://jsonplaceholder.typicode.com/todos");
    const data = await response.json();
    tasks.value = data.map((task) => task.title);
  } catch (error) {
    console.log(error);
  }
});



</script>
<template>
  <div>
    <h2>{{ name }}</h2>
    <p v-if="status === 'active'">User is active</p>
    <p v-else-if="status == 'pending'">User is Pending</p>
    <p v-else>User is Inactive</p>
  </div>

  <div>
    <h3>Tasks</h3>
    <ul>
      <li v-for="(task, index) in tasks" :key="task">
        <span>{{ task }}</span> <button @click="deleteTask(index)">x</button>
      </li>
    </ul>
  </div>

  <form @submit.prevent="addTask">
    <label for="">Name</label>
    <input type="text" v-model="newTask" id="newTask" name="newTask" />
    <button type="submit">Add Task</button>
  </form>

  <button v-on:click="toggleStatus()">Change Status</button>
  <button @click="toggleStatus()">Change Status</button>
</template>

<style scoped></style>
