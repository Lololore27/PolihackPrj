<template>
    <v-card class="rounded-lg mt-n2 pb-1" >
      <v-toolbar flat color="transparent">
      </v-toolbar>
      <v-card
        color="purple-lighten-2"
        class="rounded-lg mx-2 pa-1 mt-n3 gradient flip"
        flat
      >
      <v-card-title class="text-h6">Leaderboard</v-card-title>
      <v-divider></v-divider>
      <v-list style="background: transparent">
        <v-list-item v-for="(player, index) in sortedPlayers" :key="index">
          <v-list-item-content>
            <v-list-item-title>{{ index + 1 }}. {{ player.name }}</v-list-item-title>
          </v-list-item-content>
          <v-list-item-action>
            <span>{{ player.points }} Pts</span>
          </v-list-item-action>
        </v-list-item>
      </v-list>
        
      </v-card>
     
           
      <v-card
        class="rounded-lg mx-2 mt-1 gradient flip"
        flat
      >  
        <h2 class="white--text ml-4">Don't get discouraged</h2>
  
        <span class="grey--text mt-4 ml-4 caption"
          >“The man who moves a mountain </span
        ><br />
        <span class="grey--text ml-4 caption">begins by carrying away small stones.”</span>
  
        <v-card-text class="pt-0 mt-5">
          <router-link to="/MySpace">
          <v-btn color="#524EED" dark class="withoutupercase mt-2" 
            >Check your points</v-btn
          ></router-link>
        </v-card-text>...
       </v-card>
       
    </v-card>
  </template>
  
  <script>
  export default {
  data() {
    return {
      players: [
        { name: "Raul", points: 2864 },
        { name: "Bob", points: 160 },
        { name: "Lore", points: 250 },
         { name: "Mekky", points: 180},
         {  name: "Lari", points: 350},
        
      ],
    };
  },
  computed: {
    sortedPlayers() {
      // Sort players by points in descending order
      return [...this.players].sort((a, b) => b.points - a.points);
    },
  },
};
  </script>

  <style>
  .gradient {
    background: rgb(63, 94, 251);
    background: radial-gradient(
      circle,
      rgb(193, 162, 232) 0%,
      rgb(141, 70, 217) 100%
    );
  }
  
  

  </style> 