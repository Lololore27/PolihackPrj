<template>
    <v-app>
      <!-- Secțiunea cu imaginea de fundal -->
      <v-container fluid class="px-0 py-0">
        <v-sheet height="100vh" class="d-flex align-center" style="position: relative;">
          <!-- Imagine de fundal -->
          <v-img
            src="https://media.gettyimages.com/id/1027020436/video/timelapse-of-the-sky.jpg?s=640x640&k=20&c=1WJo-EVoLbGW6pS_NDoLxFkCEQU_GE1SZtgNd56ZU9k="
            class="fill-height"
            cover
          ></v-img>
  
          <!-- Text peste imagine -->
          <div class="overlay-text">
            <h1 class="display-1 font-weight-bold black--text">
              Step Out of Your Comfort Zone
            </h1>
            <p class="subtitle-1 text--black">
              Discover hobbies, track your progress, and find the motivation to grow every day.
            </p>
          </div>
        </v-sheet>
      </v-container>
  
      <!-- Secțiunea cu carduri -->
      <v-container class="py-8">
        <h2 class="text-center mb-8">What We Offer</h2>
  
        <v-row justify="center" align="center" dense>
          <!-- Card 1 -->
          <v-col cols="12" md="4">
            <v-card elevation="2" class="pa-6 text-center">
              <v-icon size="48" color="primary">mdi-lightbulb-on-outline</v-icon>
              <h3>Motivation</h3>
              <p>
                Get inspired to push past your limits and explore new opportunities.
              </p>
            </v-card>
          </v-col>
  
          <!-- Card 2 -->
          <v-col cols="12" md="4">
            <v-card elevation="2" class="pa-6 text-center">
              <v-icon size="48" color="primary">mdi-chart-line</v-icon>
              <h3>Tracking</h3>
              <p>
                Keep track of your hobbies, goals, and achievements in one place.
              </p>
            </v-card>
          </v-col>
  
          <!-- Card 3 -->
          <v-col cols="12" md="4">
            <v-card elevation="2" class="pa-6 text-center">
              <v-icon size="48" color="primary">mdi-lightbulb-outline</v-icon>
              <h3>Ideas</h3>
              <p>
                Discover unique hobby ideas and activities to challenge yourself.
              </p>
            </v-card>
          </v-col>
        </v-row>
      </v-container>

           <!-- Secțiunea Why -->
    <v-container class="py-8">
      <h2 class="text-center mb-8">Why?</h2>

      <v-row justify="center" align="center" dense>
        <v-col cols="12" md="4">
          <v-card elevation="2" class="pa-6 text-center">
            <v-icon size="48" color="secondary">mdi-account-group</v-icon>
            <h3>Better Social Life</h3>
            <p>
              Engaging in hobbies helps you connect with like-minded people and build meaningful relationships.
            </p>
          </v-card>
        </v-col>

        <v-col cols="12" md="4">
          <v-card elevation="2" class="pa-6 text-center">
            <v-icon size="48" color="secondary">mdi-brain</v-icon>
            <h3>Mental Health</h3>
            <p>
              Trying new things and stepping out of your comfort zone improves mental resilience and reduces stress.
            </p>
          </v-card>
        </v-col>

        <v-col cols="12" md="4">
          <v-card elevation="2" class="pa-6 text-center">
            <v-icon size="48" color="secondary">mdi-rocket-outline</v-icon>
            <h3>Personal Growth</h3>
            <p>
              Exploring hobbies and tracking progress helps you grow into the best version of yourself.
            </p>
          </v-card>
        </v-col>
      </v-row>
    </v-container>

  
     <!-- Secțiunea de apel la acțiune -->
    <v-container class="py-16 text-center" style="background: linear-gradient(135deg, #FF6B6B, #FFD93D); color: white;">
      <h2 class="special-font mb-6">
        Are you interested?
      </h2>
      <p class="text-h6 mb-8">
        Join us today and take the first step towards becoming the best version of yourself.
      </p>
      <v-btn
        color="white"
        large
        rounded
        elevation="2"
        class="pa-6 text-h5 font-weight-bold"
        @click="redirectToSignUp"
        style="color: #FF6B6B;"
      >
        Join Now
      </v-btn>
    </v-container>

    </v-app>
  </template>
  


  <script>
  export default {
    methods: {
      redirectToSignUp() {
        this.$router.push(''); // Înlocuiește cu ruta paginii de înregistrare
      },
    },
  };
  </script>
  
  <style scoped>
  /* Imaginea de fundal */
  .overlay-text {
    position: absolute;
    left: 10%;
    color: white;
    max-width: 40%;
  }
  
  /* Aliniere pentru text și carduri */
  h1, h2 {
    margin-bottom: 16px;
  }
  p {
    margin-bottom: 12px;
    line-height: 1.6;
  }
   /* Font special pentru titlu */
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@700&display=swap');

.special-font {
  font-family: 'Poppins', sans-serif;
  font-size: 3.5rem;
  line-height: 1.2;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.4);
}

/* Text descriptiv */
.text-h6 {
  font-size: 1.25rem;
  line-height: 1.8;
  max-width: 600px;
  margin: 0 auto;
}

  </style>
  
