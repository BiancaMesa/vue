<!-- We have to use export default so we have access to our methods in template -->
<script>
  export default {
    data() {
      return {
        name: "John Doe", 
        status: true,
        statusTwo: "pending",
        tasks: ['Task One', 'Task Two', 'Task Three'], 
        link: "https://google.com",
      };
    },

    methods: {
      toggleStatus() {
        if (this.statusTwo === "active") {
          this.statusTwo = "pending";
        } else if (this.statusTwo === "pending") {
          this.statusTwo = "inactive";
        } else {
          this.statusTwo = "active";
        }
      }
    }
  };
</script>

<template>
  <h1>{{ name }}</h1>

  <p v-if="status">User is active</p>
  <p v-else>User is inactive</p>

  <p v-if="statusTwo === 'active'">User is active</p>
  <p v-else-if="statusTwo === 'pending'">User is pending</p>
  <p v-else>User is inactive</p>

  <h3>Tasks:</h3>
  <ul>
    <li v-for="task in tasks" :key="task">{{ task }}</li>
  </ul>

  <a v-bind:href="link">Click for Google</a>

  <br />
  <button v-on:click="toggleStatus">Change Status</button>
</template>

