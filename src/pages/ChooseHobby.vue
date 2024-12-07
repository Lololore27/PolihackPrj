<template>
    <v-container>
      <v-row justify="center" align="center">
        <!-- Main Card Container -->
        <v-col cols="12" md="8">
          <v-card>
            <v-card-title class="text-center">
              <span class="text-h4 font-weight-bold">What hobby would you like to practice?</span>
            </v-card-title>
  
            <v-card-text>
              <!-- Interest Chips (Select one interest) -->
              <v-chip-group v-model="selectedInterest">
                <v-chip
                  v-for="interest in interests"
                  :key="interest"
                  class="mb-2"
                  color="primary"
                  text-color="white"
                  @click="filterHobbies(interest)"
                >
                  {{ interest }}
                </v-chip>
              </v-chip-group>
  
              <v-row>
                <v-col v-if="filteredHobbies.length > 0" cols="12" md="12">
                  <!-- Display hobbies as radio buttons (allow selection of one hobby only) -->
                  <v-radio-group v-model="selectedHobby" column>
                    <v-radio
                      v-for="(hobby, index) in filteredHobbies"
                      :key="index"
                      :label="hobby"
                      :value="hobby"
                    ></v-radio>
                  </v-radio-group>
                </v-col>
              </v-row>
  
              <!-- Continue Button -->
              <v-btn
                @click="continue"
                color="primary"
                block
                class="mt-4"
                :disabled="!selectedHobby"
              >
                Continue
              </v-btn>
              <!-- Section for "Things others recommend" -->
              <v-card-title class="text-h4 text-center mt-6 font-weight-bold">
                Things others recommend
              </v-card-title>
              <v-list>
                <v-list-item>
                  <v-btn
                    color="secondary"
                    block
                    @click="handleRecommendationClick('Optiunea 1')"
                  >
                    Optiunea 1
                  </v-btn>
                </v-list-item>
                <v-list-item>
                  <v-btn
                    color="secondary"
                    block
                    @click="handleRecommendationClick('Optiunea 2')"
                  >
                    Optiunea 2
                  </v-btn>
                </v-list-item>
                <v-list-item>
                  <v-btn
                    color="secondary"
                    block
                    @click="handleRecommendationClick('Optiunea 3')"
                  >
                    Optiunea 3
                  </v-btn>
                </v-list-item>
              </v-list>
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
        // Currently selected interest and hobby
        selectedInterest: null,
        selectedHobby: null,
        
        // Available interests and their corresponding hobbies
        interests: ["Sports", "Music", "Technology", "Art", "Reading"],
        hobbies: {
          Sports: ["Football", "Basketball", "Tennis", "Running", "Swimming"],
          Music: ["Guitar", "Singing", "Drums", "Piano", "DJing"],
          Technology: ["Coding", "AI", "Robotics", "Gaming", "Web Development"],
          Art: ["Painting", "Drawing", "Sculpting", "Photography", "Pottery"],
          Reading: ["Fiction", "Non-Fiction", "Science", "History", "Philosophy"],
        },
  
        filteredHobbies: [], // Hobbies to display based on selected interest
      };
    },
    methods: {
      // Filter hobbies based on selected interest
      filterHobbies(interest) {
        this.selectedInterest = interest; // Set the selected interest
        this.filteredHobbies = this.hobbies[interest]; // Set filtered hobbies based on selected interest
        this.selectedHobby = null; // Reset the selected hobby when a new interest is selected
      },
  
      // Handle continue button click
      continue() {
        alert(`You selected the hobby: ${this.selectedHobby} under the interest: ${this.selectedInterest}`);
      },
  
      // Handle click event for recommendations
      handleRecommendationClick(option) {
        alert(`You selected: ${option}`);
      }
    }
  };
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
  