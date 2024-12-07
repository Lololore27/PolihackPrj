<script setup lang="ts">
import Overview from '@/components/Overview.vue';
</script>

<template>
    <v-app
      id="inspire"
    >
      <SideBar />
      <v-container>
        <Navbar />
        <v-row>
          <v-col cols="12" sm="8">
            <v-row>
              <v-col cols="12" sm="12">
                <Overview></Overview>
                <ShareWyd></ShareWyd>
              </v-col>
              <v-col cols="12" sm="12">
                <Payment />
              </v-col>
            </v-row>
          </v-col>
          <v-col cols="12" sm="4">
            <RightDrawer/>
          </v-col>
          <PracticeHobbyIf></PracticeHobbyIf>
          <TrySomethingNew></TrySomethingNew>
        </v-row>
      </v-container>
    </v-app>
  </template>