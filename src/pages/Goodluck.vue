
<template>
    <v-container class="text-center my-12">
      <v-card class="mx-auto pa-12" max-width="800" style="min-height: 300px;">
        <v-card-title class="display-1 font-weight-bold text-wrap text-center">
          Goodluck achieving your goals today!!
        </v-card-title>
        <v-card-actions class="justify-center mt-8">
          <v-btn color="primary" large @click="onTaskComplete">
            I finished this task
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-container>
  </template>
  
  <script>
  export default {
    methods: {
      onTaskComplete() {
        alert("Congratulations on completing your task!");
      },
    },
  };
  </script>
  
  <style scoped>
  .display-1 {
    font-size: 3rem; /* Larger text size */
  }
  .text-wrap {
    word-wrap: break-word;
  }
  </style>
  