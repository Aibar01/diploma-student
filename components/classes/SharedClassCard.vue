<template>
  <v-card class="mb-1 mr-md-auto" max-width="320">
    <v-img
      class="white--text align-end"
      height="150px"
      width="320px"
      src="https://images.theconversation.com/files/362834/original/file-20201012-20-wfc3qi.jpg?ixlib=rb-1.1.0&rect=97%2C135%2C4804%2C3493&q=45&auto=format&w=496&fit=clip"
    >
    </v-img>

    <v-card-title class="pb-0"> Introduction to Scratch </v-card-title>
    <v-card-subtitle class="pt-5 pb-0">
      Introduction to Scratch
    </v-card-subtitle>

    <v-card-actions class="pt-0">
      <v-spacer />
      <v-dialog v-model="dialog" max-width="750">
        <template #activator="{ on, attrs }">
          <v-btn color="#353232" text v-bind="attrs" v-on="on">
            Join now
          </v-btn>
        </template>
        <v-card class="mx-auto" max-width="750">
          <v-img
            class="white--text align-end"
            height="400px"
            src="https://www.thoughtco.com/thmb/afe2vnJsNPE796r9o5Kd0FlwQzM=/2290x1288/smart/filters:no_upscale()/Study_Partner-56be2a453df78c0b1389e33a.jpg"
          >
          </v-img>
          <v-card-title
            class="mt-8 pr-10"
            style="position: absolute; right: 0; top: 310px"
          >
            <v-spacer></v-spacer>
            <div id="avatar">
              <v-avatar size="80">
                <img
                  alt="user"
                  src="https://img.freepik.com/free-photo/handsome-young-businessman-in-shirt-and-eyeglasses_85574-6228.jpg?size=626&ext=jpg"
                />
              </v-avatar>
              <v-card-title class="pb-4 pt-1 px-0">John Doe.</v-card-title>
              <v-card-subtitle>Programming мұғалым</v-card-subtitle>
            </div>
          </v-card-title>
          <v-card-title class="pb-0"> Introduction to Scratch </v-card-title>
          <v-card-subtitle id="card-description" class="pt-4">
            Build skills with courses, certificates, and degrees online from
            world-class universities and companies.
          </v-card-subtitle>

          <v-card-text class="text--primary">
            <div id="class-overview">
              <div>
                <v-icon color="#C4C4C4" small class="pb-1">
                  mdi-checkbox-blank-circle
                </v-icon>
                5 videos
              </div>
              <div>
                <v-icon color="#C4C4C4" small class="pb-1">
                  mdi-checkbox-blank-circle
                </v-icon>
                English
              </div>
              <div>
                <v-icon color="#C4C4C4" small class="pb-1">
                  mdi-checkbox-blank-circle
                </v-icon>
                45 min
              </div>
            </div>
          </v-card-text>
          <v-card-actions class="pb-6">
            <v-btn class="text-capitalize" dark color="#353232">
              <strong class="px-3">Join Class</strong>
            </v-btn>
          </v-card-actions>
          <v-divider class="pb-2"></v-divider>
          <v-card-actions>
            <!-- <v-btn color="black" text @click="dialog = false">
              <strong>About course</strong>
            </v-btn> -->
            <v-dialog v-model="subDialog" width="750">
              <template #activator="{ on, attrs }">
                <v-btn color="black" text v-bind="attrs" v-on="on">
                  <strong>About course</strong>
                </v-btn>
              </template>
              <v-card>
                <v-app-bar>
                  <v-toolbar-title>Introduction to Scratch</v-toolbar-title>

                  <v-spacer></v-spacer>

                  <v-btn icon @click="subDialog = false">
                    <v-icon>mdi-close</v-icon>
                  </v-btn>
                </v-app-bar>
                <div>
                  <v-container>
                    <v-row>
                      <v-col lg="3">
                        <p class="text-uppercase font-weight-bold">
                          About course
                        </p>
                      </v-col>
                      <v-col lg="9" class="text--686868"
                        >This is the second of a two-course sequence introducing
                        the fundamentals of Bayesian statistics. It builds on
                        the course Bayesian Statistics: From Concept to Data
                        Analysis, which introduces Bayesian methods through use
                        of simple conjugate models.
                      </v-col>
                    </v-row>
                    <v-row>
                      <v-col lg="3">
                        <p class="text-uppercase font-weight-bold">Syllabus</p>
                      </v-col>
                      <v-col lg="9" class="text--686868">
                        <v-list-item class="px-0">
                          <v-list-item-content class="pt-0">
                            <v-list-item-title
                              >1. Single-line item</v-list-item-title
                            >
                          </v-list-item-content>
                        </v-list-item>

                        <v-list-item class="px-0">
                          <v-list-item-content class="pt-0">
                            <v-list-item-title
                              >2. Two-line item</v-list-item-title
                            >
                          </v-list-item-content>
                        </v-list-item>

                        <v-list-item class="px-0">
                          <v-list-item-content class="pt-0">
                            <v-list-item-title
                              >3. Three-line item</v-list-item-title
                            >
                          </v-list-item-content>
                        </v-list-item>
                      </v-col>
                    </v-row>
                  </v-container>
                </div>
                <v-divider></v-divider>
                <v-card-actions>
                  <v-spacer></v-spacer>
                  <v-btn class="text-capitalize" dark color="#353232">
                    <strong class="px-3">Join Class</strong>
                  </v-btn>
                </v-card-actions>
              </v-card>
            </v-dialog>
            <v-card-text>
              Build skills with courses, certificates, and degrees online from
              world-class universities and companies.
            </v-card-text>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  data() {
    return {
      dialog: false,
      subDialog: false,
    }
  },
}
</script>

<style scoped>
#class-overview {
  width: 40%;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
}
#card-description {
  width: 70%;
}
#avatar {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  top: 20%;
}

#content {
  display: flex;
  flex-direction: row;
  align-content: center;
}
</style>
