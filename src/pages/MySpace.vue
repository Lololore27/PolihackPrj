<template>
    <v-container>
      <!-- HEADER -->
      <v-row class="text-center mb-6">
        <v-col cols="12">
          <v-sheet rounded="xl" elevation="3" class="pa-6" color="purple-lighten-3">
            <h1 class="display-1 font-weight-bold text-white">My Space</h1>
            <p class="text-h6">
              Track your progress & more
            </p>
          </v-sheet>
        </v-col>
      </v-row>
  
      <!-- HOBBY-URI ȘI PROVOCĂRI -->
      <v-row>
        <v-col cols="12">
          <h2 class="text-h5 font-weight-bold">Explore Hobbies and Challanges</h2>
        </v-col>
  
        <!-- Card pentru un hobby -->
        <v-col cols="12" sm="6" md="4" v-for="(hobby, index) in hobbies" :key="index">
          <v-card>
            <v-card-title>{{ hobby.title }}</v-card-title>
            <v-card-text>
              {{ hobby.description }}
            </v-card-text>
            <v-card-actions>
              <v-btn color="primary" @click="startChallenge(hobby)">Try</v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
      
      <v-row class="d-flex justify-center">
    <v-col cols="12">
      <h2 class="text-h5 font-weight-bold">Here are your points</h2>
    </v-col>

    <!-- Carduri unul lângă altul -->
    <v-col cols="12" sm="6" md="6">
      <v-card
        class="mx-auto text-center"
        color="deep-purple-lighten-4"
        max-width="600"
        dark
      >
        <v-card-text>
          <v-sheet color="deep-purple-lighten-1">
            <v-sparkline
              :model-value="value"
              color="rgba(255, 255, 255, .7)"
              height="100"
              padding="24"
              stroke-linecap="round"
              smooth
            >
              <template v-slot:label="item">
                {{ day }} {{ item.value }}
              </template>
            </v-sparkline>
          </v-sheet>
        </v-card-text>

        <v-card-text>
          <div class="text-h4 font-weight-thin">
            Points achieved <br> this week
          </div>
        </v-card-text>
      </v-card>
    </v-col>

    <v-col cols="12" sm="6" md="6">
      <v-card
        class="mx-auto text-center"
        color="deep-purple-lighten-4"
        max-width="600"
        dark
      >
        <v-card-text>
          <v-sheet color="deep-purple-lighten-1">
            <h1>2864 pts</h1>
          </v-sheet>
        </v-card-text>

        <v-card-text>
          <div class="text-h4 font-weight-thin">
            Total of points
          </div>
        </v-card-text>
      </v-card>
    </v-col>
  </v-row>

  
  
      <!-- PROGRESUL PERSONAL -->
      <v-row class="mt-8">
        <v-col cols="12">
          <h2 class="text-h5 font-weight-bold">Activitate in desfasurare</h2>
        </v-col>
        <v-col cols="12">
          <v-progress-linear :value="progress" height="20" color="primary">
            {{ progress }}%
          </v-progress-linear>
          <p class="mt-2">
            Ai completat {{ progress }}% din provocările tale!
          </p>
        </v-col>
      </v-row>
  
      <!-- LISTĂ DE ACTIVITĂȚI -->
      <v-row class="mt-8">
        <v-col cols="12">
          <h2 class="text-h5 font-weight-bold">My activities</h2>
        </v-col>
        <v-col cols="12">
          <v-list>
            <v-list-item v-for="(activity, index) in activities" :key="index">
              <v-list-item-content>
                <v-list-item-title>{{ activity }}</v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list>
        </v-col>
      </v-row>
  
      <!-- BUTON DE ACȚIUNE -->
      <v-btn
        class="mt-6"
        color="purple-lighten-2"
        large
        block
        @click="addNewChallenge"
      >
      Add an activity
      </v-btn>
    </v-container>
  </template>
  
  
   <script setup>
import { ref } from 'vue';

// Date pentru grafic
const labels = ref([
  '12am',
  '3am',
  '6am',
  '9am',
  '12pm',
  '3pm',
  '6pm',
  '9pm',
]);

const value = ref([
  200,
  675,
  410,
  390,
  310,
  460,
  250,
]);

// Hobby-uri
const hobbies = ref([
  { title: "Painting", description: "Paint your emotions away. Free your mind" },
  { title: "Hiking", description: "Reconnect with nature" },
  { title: "Dancing", description: "Find a welcoming comunity while exercising your phisical " },
]);

// Progres
const progress = ref(60); // procentajul progresului completat

// Activități noi
const activities = ref([
  "Paint the first thing you see",
  "Citește o carte într-un domen",
  "Încearcă un sport extrem.",
]);

// Funcții
const startChallenge = (hobby) => {
  alert(`Ai început hobby-ul: ${hobby.title}`);
};

const addNewChallenge = () => {
  const newActivity = prompt("Introdu o nouă activitate:");
  if (newActivity) activities.value.push(newActivity);
};

const daysOfWeek = ref([
  'Luni',
  'Marți',
  'Miercuri',
  'Joi',
  'Vineri',
  'Sâmbătă',
  'Duminică',
]);


  </script>

  
  <style scoped>
  .text-caption {
    font-size: 0.8rem;
    font-weight: bold;
  }
  </style>
  