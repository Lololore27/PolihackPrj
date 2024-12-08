<template>
    
    <v-form>
    <v-container>
      <v-row>
        <v-col cols="12">
          <v-text-field
            v-model="message"
            :append-icon="message ? 'mdi-send' : 'mdi-microphone'"
            :prepend-icon="icon"
            clear-icon="mdi-close-circle"
            label="Message"
            type="text"
            variant="filled"
            clearable
            @click:append="sendMessage"
            @click:append-inner="toggleMarker"
            @click:clear="clearMessage"
            @click:prepend="changeIcon"
          ></v-text-field>
        </v-col>
      </v-row>
    </v-container>
  </v-form>

    <v-card
        class="mt-4"
        outlined
        max-width="400"
      >
        <v-card-text>
          Acesta este cardul cu un mesaj de exemplu.
        </v-card-text>
      </v-card>

  </template>
  <script>
  export default {
    data() {
      return {
        message: '',
        marker: false,
        icon: 'mdi-email',
      };
    },
    methods: {
      sendMessage() {
        console.log('Trimite mesaj:', this.message);
      },
      toggleMarker() {
        this.marker = !this.marker;
      },
      clearMessage() {
        this.message = '';
      },
      changeIcon() {
        this.icon = this.icon === 'mdi-email' ? 'mdi-account' : 'mdi-email';
      },
    },
  };
  </script>
  
  <style>
  .fill-height {
    height: 100vh;
  }
  </style>