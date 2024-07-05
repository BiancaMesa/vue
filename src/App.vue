<!-- We have to use export default so we have access to our methods in template -->
<script setup>
import { ref } from "vue"; 

      const name = ref ("John Doe"); 
      const status = ref ("active");
      const tasks = ref (["Task One", "Task Two", "Task Three"]);
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
        //Validation
        if (newTask.value.trim() !== "") {
          tasks.value.push(newTask.value);
          newTask.value = "";
        }
      };
</script>

<!-- <script>
import { ref } from "vue"; 

  export default {
    setup() {
      const name = ref ("John Doe"); 
      const status = ref (true);
      const statusTwo = ref ("active");
      const tasks = ref (["Task One", "Task Two", "Task Three"]);

      const toggleStatus = () => {
        if (statusTwo.value === "active") {
          statusTwo.value = "pending";
        } else if (statusTwo.value === "pending") {
          statusTwo.value = "inactive";
        } else {
          statusTwo.value = "active";
        }
      }

      return {
        name, 
        status, 
        statusTwo,
        tasks, 
        toggleStatus
      }
    }
  };
</script> -->

<template>
  <h1>{{ name }}</h1>

  <p v-if="status === 'active'">User is active</p>
  <p v-else-if="status === 'pending'">User is pending</p>
  <p v-else>User is inactive</p>

  <form @submit.prevent="addTask">
    <label for="newTask">Add Task</label>
    <input type="text" id="newTask" name="newTask" v-model="newTask">
    <button type="submit">Submit</button>
  </form>

  <h3>Tasks:</h3>
  <ul>
    <li v-for="task in tasks" :key="task">
      {{ task }}
    </li>
  </ul>


  <br />
  <button v-on:click="toggleStatus">Change Status</button>
</template>

