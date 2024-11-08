// Options API

<script>
export default {
  data() {
    return {
      name: "John Doe",
      status: "active",
      tasks: ["Task one", "Task two", "Task three"],
      link: "https://google.com",
    };
  },
  methods: {
    togleStatus() {
      // this.status = this.status === "active" ? "pending" : "active";

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
  <h1>{{ name }}</h1>
  <!-- <p v-if="status">User is active</p>
  <p v-else>User is not active</p> -->
  <p v-if="status === 'active'">User is active</p>
  <p v-else-if="status === 'pending'">User is pending</p>
  <p v-else>User is not active</p>

  <h3>Tasks</h3>
  <ul>
    <li v-for="task in tasks" :key="task">{{ task }}</li>
  </ul>

  <!-- <a v-bind:href="link">Clik here</a> -->
  <a :href="link">Clik here</a>
  <br />

  <!-- <button v-on:click="togleStatus">Change status</button> -->
  <button @click="togleStatus">Change status</button>
</template>

<!-- Compostion API -->
<script setup>
import { ref } from "vue";

const name = ref("John");
const status = ref("active");
const tasks = ref(["task 1", "task 2", "task 3"]);
const link = ref("https://google.com");

const newTask = ref("");
const togleStatus = () => {
  // status.value = status.value === "active" ? "pending" : "active";
  if (this.status === "active") {
    this.status = "pending";
  } else if (this.status === "pending") {
    this.status = "inactive";
  } else {
    this.status = "active";
  }
};

const addTask = () => {
  if (newTask.value.trim() !== "") {
    tasks.value.push(newTask.value);
    newTask.value = "";
  }
};

const deleteTask = (index) => {
  tasks.value.splice(index, 1);
};
</script>

<template>
  <h1>{{ name }}</h1>
  <!-- <p v-if="status">User is active</p>
  <p v-else>User is not active</p> -->
  <p v-if="status === 'active'">User is active</p>
  <p v-else-if="status === 'pending'">User is pending</p>
  <p v-else>User is not active</p>

  <form @submit.prevent="addTask">
    <label for="newTask">Add Task</label>
    <input type="text" id="newTask" v-model="newTask" />
    <button type="submit">Submit</button>
  </form>

  <h3>Tasks</h3>
  <ul>
    <li v-for="(task, index) in tasks" :key="task">
      <span>{{ task }}</span>
      <button @click="deleteTask(index)">Delete</button>
    </li>
  </ul>

  <!-- <a v-bind:href="link">Clik here</a> -->
  <a :href="link">Clik here</a>
  <br />

  <!-- <button v-on:click="togleStatus">Change status</button> -->
  <button @click="togleStatus">Change status</button>
</template>
