<script setup lang="ts">
import AskCosticaAi from '@/components/AskCosticaAi.vue';
import Overview from '@/components/Overview.vue';
import { computed, ref } from 'vue';

const option = ref("option_one");

function doSomething(newOption) {
  option.value = newOption;
}

</script>

<template>
    <v-app
      id="inspire"
    >
      <v-container>
        <Navbar />
        <v-row>
          <v-col cols="12" sm="8">
            <v-row>
              <v-col cols="12" sm="12">
                <Overview></Overview>
                <ShareWyd @option-changed="doSomething"></ShareWyd>
              </v-col>
              <v-col cols="12" sm="12">
                <Payment />
              </v-col>
            </v-row>
          </v-col>
          <v-col cols="12" sm="4">
            <RightDrawer/>
          </v-col>
          <PracticeHobbyIf v-if="option === 'option_one'"></PracticeHobbyIf>
          <TrySomethingNew v-if="false"></TrySomethingNew>
          <AskCosticaAi></AskCosticaAi>

        </v-row>
      </v-container>
    </v-app>
  </template>