<template>
    <v-container>
      <v-row justify="center" align="center">
        <!-- Main Card Container -->
        <v-col cols="12" md="8">
              <!-- Section for "Things others recommend" -->
              <v-card-title class="text-h4 text-center mt-6 font-weight-bold">
                Things others recommend
              </v-card-title>
              <v-list>
                <v-list-item>
                  <v-btn
                    color="deep-purple-accent-1"
                    block
                    @click="handleRecommendationClick('Optiunea 1')"
                  >
                    Optiunea 1
                  </v-btn>
                </v-list-item>
                <v-list-item>
                  <v-btn
                    color="deep-purple-accent-1"
                    block
                    @click="handleRecommendationClick('Optiunea 2')"
                  >
                    Optiunea 2
                  </v-btn>
                </v-list-item>
                <v-list-item>
                  <v-btn
                    color="deep-purple-accent-1"
                    block
                    @click="handleRecommendationClick('Optiunea 3')"
                  >
                    Optiunea 3
                  </v-btn>
                </v-list-item>
              </v-list>
        </v-col>
      </v-row>
    </v-container>
  </template>
  
  <script>
  export default {
    data() {
      return {

    methods: {
      // Handle click event for recommendations
      handleRecommendationClick(option) {
        alert(`You selected: ${option}`);
      }
    }
  };}}
  </script>
  
  <style scoped>
  .v-card {
    padding: 20px;
  }
  .v-chip {
    cursor: pointer;
  }
  .v-btn {
    margin-top: 10px;
  }
  </style>
  