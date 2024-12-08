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
                    @click="handleRecommendationClick(1)"
                  >
                    {{ opt1 }}
                  </v-btn>
                </v-list-item>
                <v-list-item>
                  <v-btn
                    color="deep-purple-accent-1"
                    block
                    @click="handleRecommendationClick(2)"
                  >
                  {{ opt2 }}
                  </v-btn>
                </v-list-item>
                <v-list-item>
                  <v-btn
                    color="deep-purple-accent-1"
                    block
                    @click="handleRecommendationClick(3)"
                  >
                  {{ opt3 }}
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
        URLQ: "http://localhost:8080/users/tasked",
        URLP: "http://localhost:8080/users/points",
        opt1: null,
        opt2: null,
        opt3: null ,
        respo: null,
        finalopt: null,
      }
    },

    mounted() {
    // Run function after component is mounted (element is in DOM)
    this.getPosted();
    },

    methods: {
      // Handle click event for recommendations
      async getPosted() {
      try {
        // POST request to the API endpoint
        const response = await fetch(this.URLQ, {
          method: "POST",
          headers: {
            "Content-Type": "application/json",
          },
        });
        this.respo = await response.json(); console.log(this.respo)
        this.opt1=this.respo.un;this.opt2=this.respo.doi;this.opt3=this.respo.tri;
      } catch (err) {
        alert(err);
      }
    },

     async handleRecommendationClick(option) {
        try {
          const response = await fetch(this.URLP, {
            method: "POST",
            headers: {
              "Content-Type": "application/json",
            },
            body:{
              "username":"Raul",
              "points": option
            }
          })
        }catch (err){
          alert(err)
        }
        console.log(response.json())
      },
    },
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
  