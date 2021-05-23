<template>
  <v-card elevation="0" outlined class="mb-1 mr-md-auto" max-width="320">
    <nuxt-img
      v-if="item.class_image"
      class="white--text align-end"
      height="150px"
      width="320px"
      :src="item.class_image"
      format="webp"
    />
    <nuxt-img
      v-else
      class="white--text align-end"
      height="150px"
      width="320px"
      src="https://images.theconversation.com/files/362834/original/file-20201012-20-wfc3qi.jpg?ixlib=rb-1.1.0&rect=97%2C135%2C4804%2C3493&q=45&auto=format&w=496&fit=clip"
      format="webp"
    />
    <v-card-title class="pb-0 font-weight-bold">
      {{ item.class_name }}
    </v-card-title>
    <v-card-subtitle class="pt-5 pb-0">
      {{ item.teacher.first_name }} {{ item.teacher.last_name }}
    </v-card-subtitle>
    <v-card-subtitle class="pb-0 pt-1">
      {{ item.subject }}
    </v-card-subtitle>

    <v-card-actions class="pt-0">
      <v-spacer />
      <v-dialog v-model="dialog" max-width="750">
        <template #activator="{ on, attrs }">
          <v-btn color="#353232" text elevation="0" v-bind="attrs" v-on="on">
            Қосылу
          </v-btn>
        </template>
        <v-card class="mx-auto" max-width="750">
          <v-img
            v-if="item.class_image"
            class="white--text align-end"
            height="400px"
            :src="item.class_image"
          />
          <v-img
            v-else
            class="white--text align-end"
            height="400px"
            src="https://images.theconversation.com/files/362834/original/file-20201012-20-wfc3qi.jpg?ixlib=rb-1.1.0&rect=97%2C135%2C4804%2C3493&q=45&auto=format&w=496&fit=clip"
          />
          <v-card-title
            class="mt-8 pr-10"
            style="position: absolute; right: 0; top: 310px"
          >
            <v-spacer></v-spacer>
            <div id="avatar">
              <v-avatar size="80">
                <img alt="user" :src="item.teacher.avatar" />
              </v-avatar>
              <v-card-title class="pb-4 pt-1 px-0"
                >{{ item.teacher.first_name }}
                {{ item.teacher.last_name }}</v-card-title
              >
              <v-card-subtitle>Mұғалым</v-card-subtitle>
            </div>
          </v-card-title>
          <v-card-title class="pb-0 font-weight-bold">
            {{ item.class_name }}
          </v-card-title>
          <v-card-subtitle id="card-description" class="pt-4">
            {{ item.subject }}
          </v-card-subtitle>

          <v-card-text class="text--primary">
            <div id="class-overview">
              <div v-for="prop in item.syllabus" :key="prop">
                <v-icon color="#C4C4C4" small class="pb-1">
                  mdi-checkbox-blank-circle
                </v-icon>
                {{ prop }}
              </div>
            </div>
          </v-card-text>
          <v-card-actions class="pb-6">
            <v-btn
              elevation="0"
              class="text-capitalize"
              dark
              color="#353232"
              @click="joinClass"
            >
              <strong class="px-3">Қосылу</strong>
            </v-btn>
          </v-card-actions>
          <v-divider v-if="item.about_course" class="pb-2"></v-divider>
          <v-card-actions v-if="item.about_course">
            <!-- <v-btn color="black" text @click="dialog = false">
              <strong>About course</strong>
            </v-btn> -->
            <v-dialog v-model="subDialog" width="750">
              <template #activator="{ on, attrs }">
                <v-btn color="black" text v-bind="attrs" v-on="on">
                  <strong>Сынып туралы</strong>
                </v-btn>
              </template>
              <v-card>
                <v-app-bar>
                  <v-toolbar-title>{{ item.class_name }}</v-toolbar-title>

                  <v-spacer></v-spacer>

                  <v-btn icon @click="subDialog = false">
                    <v-icon>mdi-close</v-icon>
                  </v-btn>
                </v-app-bar>
                <div>
                  <v-container>
                    <v-row v-if="item.about_course">
                      <v-col lg="3">
                        <p class="text-uppercase font-weight-bold">
                          Курс туралы
                        </p>
                      </v-col>
                      <v-col lg="9" class="text--686868"
                        >{{ item.about_course }}
                      </v-col>
                    </v-row>
                    <v-row>
                      <v-col lg="3">
                        <p class="text-uppercase font-weight-bold">Силлабус</p>
                      </v-col>
                      <v-col lg="9" class="text--686868">
                        <v-list-item
                          v-for="prop in item.syllabus"
                          :key="prop"
                          class="px-0"
                        >
                          <v-list-item-content class="pt-0">
                            <v-list-item-title>{{ prop }}</v-list-item-title>
                          </v-list-item-content>
                        </v-list-item>
                      </v-col>
                    </v-row>
                  </v-container>
                </div>
                <v-divider></v-divider>
                <v-card-actions>
                  <v-spacer></v-spacer>
                  <v-btn
                    elevation="0"
                    class="text-capitalize"
                    dark
                    color="#353232"
                    @click="joinClass"
                  >
                    <strong class="px-3">Қосылу</strong>
                  </v-btn>
                </v-card-actions>
              </v-card>
            </v-dialog>
            <v-card-text v-if="item.about_course">
              {{ item.about_course.split('.')[0] }}.
            </v-card-text>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      dialog: false,
      subDialog: false,
    }
  },
  methods: {
    async joinClass() {
      const ids = [this.$auth.user.id]
      try {
        ids.concat(this.item.students)

        await this.$axios.$patch(`/classes/class/${this.item.id}/`, {
          students: ids,
        })

        this.dialog = false
        this.$router.push(`class/${this.item.id}/stream`)
      } catch (err) {
        // eslint-disable-next-line no-console
        console.log(err)
      }
    },
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
