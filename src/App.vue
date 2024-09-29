<script>
export default {
  data() {
    return {
      name: "Fraz Shabbir",
      status: "active",
      tasks: ["Task 1", "Task 2", "Task 3"],
      link: "https://www.google.com",
    };
  },
  methods: {
    toggleStatus() {
      if (this.status === "active") {
        this.status = "pending";
      } else if (this.status === "pending") {
        this.status = "inactive";
      } else {
        this.status = "active";
      }
    },
  },
};
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
      <li v-for="task in tasks" :key="task">{{ task }}</li>
    </ul>
  </div>

  <a v-bind:href="link">Google</a>
  <button v-on:click="toggleStatus()">Change Status</button>
  <button @click="toggleStatus()">Change Status</button>
</template>

<style scoped></style>
