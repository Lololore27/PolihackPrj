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
                <Overview />
              </v-col>
              <v-col cols="12" sm="12">
                <Money />
              </v-col>
              <v-col cols="12" sm="12">
                <Payment />
              </v-col>
            </v-row>
          </v-col>
          <v-col cols="12" sm="4">
            <RightDrawer/>
          </v-col>
        </v-row>
      </v-container>
    </v-app>
  </template>