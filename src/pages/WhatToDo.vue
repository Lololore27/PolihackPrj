<template>
    <v-container>
      <v-row justify="center" align="center">
        <!-- Main Card Container -->
        <v-col cols="12" md="10">
          <v-card>
            <v-card-title class="text-center">
              <!-- Big Text with Styling -->
              <span class="text-h3 font-weight-bold blue--text text-decoration-underline">
                What hobby would you like to practice?
              </span>
            </v-card-title>
  
            <v-card-text>
              <!-- Radio Group for Options -->
              <v-radio-group v-model="selectedOption" column class="mb-6">
                <v-radio label="Hobbies you already registered" value="existing_hobbies"></v-radio>
                <v-radio label="Register new hobbies" value="new_hobbies"></v-radio>
              </v-radio-group>
  
              <!-- Send Button -->
              <v-btn @click="handleSubmit" color="primary" block>Submit</v-btn>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </template>
  
  <script>
  export default {
    data() {
      return {
        selectedOption: '', // Holds the selected radio option
      };
    },
    methods: {
      handleSubmit() {
        if (this.selectedOption) {
          alert(`You selected: ${this.selectedOption}`);
        } else {
          alert('Please select an option!');
        }
      },
    },
  };
  </script>
  
  <style scoped>
  .v-card {
    padding: 30px;
    box-shadow: 0px 4px 12px rgba(0, 0, 0, 0.1);
  }
  
  .v-btn {
    text-transform: none; /* Keeps the button text as it is */
  }
  
  .v-radio-group {
    margin-bottom: 24px;
  }
  </style>
  