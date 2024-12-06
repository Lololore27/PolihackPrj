<template>
    <v-container>
      <!-- HEADER -->
      <v-row class="text-center mb-6">
        <v-col cols="12">
          <v-sheet rounded="xl" elevation="3" class="pa-6" color="purple-lighten-1">
            <h1 class="display-1 font-weight-bold text-white">My Space</h1>
            <p class="text-h6">
              "Iesi din zona de confort și explorează noi pasiuni!"
            </p>
          </v-sheet>
        </v-col>
      </v-row>
  
      <!-- HOBBY-URI ȘI PROVOCĂRI -->
      <v-row>
        <v-col cols="12">
          <h2 class="text-h5 font-weight-bold">Explorează hobby-uri și provocări</h2>
        </v-col>
  
        <!-- Card pentru un hobby -->
        <v-col cols="12" sm="6" md="4" v-for="(hobby, index) in hobbies" :key="index">
          <v-card>
            <v-card-title>{{ hobby.title }}</v-card-title>
            <v-card-text>
              {{ hobby.description }}
            </v-card-text>
            <v-card-actions>
              <v-btn color="primary" @click="startChallenge(hobby)">Începe</v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
  
      <!-- PROGRESUL PERSONAL -->
      <v-row class="mt-8">
        <v-col cols="12">
          <h2 class="text-h5 font-weight-bold">Progresul meu</h2>
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
          <h2 class="text-h5 font-weight-bold">Activități noi de încercat</h2>
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
        color="success"
        large
        block
        @click="addNewChallenge"
      >
        Adaugă o nouă provocare
      </v-btn>
    </v-container>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  // Hobby-uri
  const hobbies = ref([
    { title: "Pictură", description: "Exploră-ți creativitatea cu un set de culori acrilice." },
    { title: "Drumeții", description: "Descoperă trasee uimitoare în natură." },
    { title: "Fotografie", description: "Captură momente unice și împărtășește frumusețea lor." },
  ]);
  
  // Progres
  const progress = ref(60); // procentajul progresului completat
  
  // Activități noi
  const activities = ref([
    "Înscrie-te la un curs de dans.",
    "Citește o carte într-un domeniu nou.",
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
  </script>
  
  <style scoped>
  h1 {
    color: #1976d2;
  }
  
  .text-center {
    text-align: center;
  }
  </style>
  