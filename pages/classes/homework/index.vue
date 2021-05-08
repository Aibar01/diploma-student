<template>
  <v-container fluid>
    <v-row class="pt-5 pl-5">
      <v-col cols="4">
        <v-card outlined max-width="500">
          <v-card-title>
            <v-list-item class="pl-0 grow">
              <v-list-item-avatar color="#10AFA7">
                <span class="white--text headline">
                  <v-icon dark>mdi-notebook</v-icon>
                </span>
              </v-list-item-avatar>

              <v-list-item-content>
                <v-list-item-title>{{ data.title }}</v-list-item-title>
                <v-list-item-subtitle>{{ data.date }}</v-list-item-subtitle>
              </v-list-item-content>
            </v-list-item>
          </v-card-title>

          <v-card-text class="pb-0 font-weight-bold">
            {{ data.content }}
          </v-card-text>

          <v-card-text class="font-weight-bold">
            Due to 15.03.2021
          </v-card-text>
        </v-card>
      </v-col>
      <v-col cols="3">
        <v-card outlined max-width="500">
          <v-card-title>
            <v-list-item class="pl-0 grow">
              <v-list-item-content>
                <div class="d-flex">
                  <v-list-item-title>Your work</v-list-item-title>
                  <div>
                    <v-spacer></v-spacer>
                    <v-list-item-subtitle>Assigned</v-list-item-subtitle>
                  </div>
                </div>
              </v-list-item-content>
            </v-list-item>
          </v-card-title>
          <v-card-text class="px-5">
            <div>
              <v-card outlined>
                <div class="d-flex">
                  <v-avatar width="100" height="75" tile>
                    <v-icon x-large class="pt-2"> mdi-file </v-icon>
                  </v-avatar>
                  <div>
                    <v-card-title class="text-h6 pl-0 pt-6"
                      >img045.ipg</v-card-title
                    >
                  </div>
                  <v-avatar width="100" height="75" tile>
                    <v-icon x-large class="pt-2 pl-8"> mdi-close </v-icon>
                  </v-avatar>
                </div>
              </v-card>
            </div>
          </v-card-text>
          <v-card-actions class="pt-0 px-5">
            <v-btn
              color="#10AFA7"
              dark
              block
              outlined
              class="text-capitalize py-7"
            >
              <v-icon class="mr-5">mdi-plus-circle-outline</v-icon>
              <div>Add attachment</div>
            </v-btn>
          </v-card-actions>
          <v-card-actions class="pt-0 pb-5 px-5">
            <v-btn color="#10AFA7" dark block class="text-capitalize py-7">
              Submit homework
            </v-btn>
          </v-card-actions>
        </v-card>
        <v-card class="mt-4" outlined>
          <v-card-title>
            <v-list-item class="pl-0 grow">
              <v-list-item-content>
                <div class="d-flex">
                  <v-list-item-title class="pl-2 text-h6 font-weight-regular"
                    >Grade</v-list-item-title
                  >
                  <div>
                    <v-spacer></v-spacer>
                    <v-list-item-subtitle class="text-h5"
                      >100/100</v-list-item-subtitle
                    >
                  </div>
                </div>
              </v-list-item-content>
            </v-list-item>
          </v-card-title>
        </v-card>
      </v-col>
    </v-row>
    <v-row class="pt-5 pl-5">
      <v-col cols="12">
        <v-card outlined max-width="500">
          <v-card-title class="py-0">
            <v-list-item class="pl-0 pr-0 grow">
              <v-list-item-content>
                <v-list-item-title class="title">Comments</v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-card-title>
          <v-divider></v-divider>
          <v-card-actions class="pb-0">
            <v-text-field
              class="pt-4 px-3"
              label="Add comments"
              outlined
            ></v-text-field>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      dialog: false,
      data: {
        title: 'Homework 1: Create character',
        content:
          'Try to make your own character in the Scratch by the methods that we learned in Lesson 1. No cheating!!!',
        date: '12 Mar 2021 at 12:01',
        type: 'notfication',
      },
      radios: ['p = 1/3', 'p = 1/2', 'p = 1/6', 'p = 5/4'],
    }
  },
}
</script>

<style scoped>
.v-input__slot {
  margin-bottom: 0;
}
</style>
