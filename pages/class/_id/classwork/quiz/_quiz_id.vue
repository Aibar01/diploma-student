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
            Дейін уақыт 15.03.2021
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

          <v-card-actions class="pt-0 pb-5 px-5">
            <v-dialog v-model="dialog" persistent max-width="600px">
              <template #activator="{ on, attrs }">
                <v-btn
                  color="#10AFA7"
                  dark
                  block
                  class="text-capitalize py-7"
                  v-bind="attrs"
                  v-on="on"
                >
                  Pass quiz
                </v-btn>
              </template>
              <v-card>
                <v-card-subtitle class="pl-9 pb-0 pt-7"
                  >Дейін уақыт: 24 March 2021, 00:00</v-card-subtitle
                >
                <v-card-title class="pl-9 pt-2">
                  <span class="headline">Quiz 1</span>
                </v-card-title>
                <v-card-subtitle class="pl-9 pt-4">3 questions</v-card-subtitle>
                <v-divider></v-divider>
                <v-card-text class="pt-2 pb-0">
                  <v-container>
                    <v-row>
                      <v-col cols="12">
                        <p class="text-h5">Find the probality</p>
                        <v-radio-group v-model="radioGroup">
                          <v-radio
                            v-for="n in radios"
                            :key="n"
                            :label="n"
                            :value="n"
                            color="#10AFA7"
                          ></v-radio>
                        </v-radio-group>
                      </v-col>
                      <v-col cols="12">
                        <p class="text-h5">
                          Choose right options regarding to the previous
                          question
                        </p>
                        <v-checkbox
                          v-for="n in 4"
                          :key="n"
                          :label="`0,${n}`"
                          color="#10AFA7"
                          :value="`0,${n}`"
                          hide-details
                        ></v-checkbox>
                      </v-col>
                      <v-col cols="12">
                        <p class="text-h5">
                          Choose right options regarding to the previous
                          question
                        </p>
                        <v-text-field
                          label="Your answer"
                          outlined
                        ></v-text-field>
                      </v-col>
                    </v-row>
                  </v-container>
                </v-card-text>
                <v-divider></v-divider>
                <v-card-actions class="pl-9 pt-8">
                  <v-btn
                    color="#C6C4C4"
                    dark
                    class="text-capitalize pa-6 subtitle-1 font-weight-regular"
                    @click="dialog = false"
                  >
                    Submit
                  </v-btn>
                  <v-btn
                    text
                    class="text-capitalize pa-6 subtitle-1"
                    @click="dialog = false"
                  >
                    Cancel
                  </v-btn>
                </v-card-actions>
              </v-card>
            </v-dialog>
          </v-card-actions>
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
          <v-card elevation="0" max-width="500">
            <v-card-title>
              <v-list-item class="pl-0 grow">
                <v-list-item-avatar color="#10AFA7">
                  <img
                    alt="Avatar"
                    src="https://avatars0.githubusercontent.com/u/9064066?v=4&s=460"
                  />
                </v-list-item-avatar>

                <v-list-item-content>
                  <v-list-item-title> Aidyn Jomart </v-list-item-title>
                  <v-list-item-subtitle>
                    14.03.2021 14:54
                  </v-list-item-subtitle>
                </v-list-item-content>
              </v-list-item>
            </v-card-title>

            <v-card-text class="pb-0 font-weight-bold">
              Great Job! I would like to ask you to share your resluts with
              others.
            </v-card-text>
          </v-card>
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
  layout(context) {
    return 'blog'
  },
  data() {
    return {
      dialog: false,
      data: {
        title: 'Quiz 1',
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
