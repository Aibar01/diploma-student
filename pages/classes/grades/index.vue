<template>
  <v-container fluid>
    <v-row class="pl-5 pt-5">
      <v-col>
        <div class="text-uppercase">Overall info</div>
      </v-col>
    </v-row>
    <v-row class="pl-5">
      <v-col cols="3">
        <v-card outlined class="mx-auto" max-width="400">
          <v-card-text>
            <v-row align="center">
              <v-col cols="6">
                <v-list-item two-line>
                  <v-list-item-content>
                    <v-list-item-title class="headline">
                      Grade
                    </v-list-item-title>
                    <v-list-item-subtitle>
                      You’re doing well!
                    </v-list-item-subtitle>
                  </v-list-item-content>
                </v-list-item>
              </v-col>
              <v-col d-flex justify="center" align="center" cols="6">
                <v-row>
                  <v-col class="display-2" cols="12">95%</v-col>
                </v-row>
              </v-col>
            </v-row>
          </v-card-text>
        </v-card>
      </v-col>
      <v-col cols="3">
        <v-card outlined class="mx-auto" max-width="400">
          <v-card-text>
            <v-row align="center">
              <v-col cols="6">
                <v-list-item two-line>
                  <v-list-item-content>
                    <v-list-item-title class="headline">
                      Homeworks
                    </v-list-item-title>
                    <v-list-item-subtitle>
                      You submitted all!
                    </v-list-item-subtitle>
                  </v-list-item-content>
                </v-list-item>
              </v-col>
              <v-col d-flex justify="center" align="center" cols="6">
                <v-row>
                  <v-col class="display-2" cols="12">1/1</v-col>
                </v-row>
              </v-col>
            </v-row>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
    <v-row class="pl-5 pt-5">
      <v-col>
        <div class="text-uppercase">All grades</div>
      </v-col>
    </v-row>
    <v-row>
      <v-col v-for="i in 6" :key="i" cols="12">
        <v-card elevation="0" max-width="800">
          <v-card-title class="pt-0">
            <v-list-item class="pl-0 grow">
              <v-list-item-avatar color="#10AFA7">
                <img
                  alt="Avatar"
                  src="https://avatars0.githubusercontent.com/u/9064066?v=4&s=460"
                />
              </v-list-item-avatar>

              <v-list-item-content>
                <div class="d-flex">
                  <v-list-item-title>
                    Homework 1: Create character
                  </v-list-item-title>
                  <v-list-item-title class="font-weight-bold">
                    95%
                  </v-list-item-title>
                </div>
              </v-list-item-content>
            </v-list-item>
          </v-card-title>
          <v-divider></v-divider>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>
