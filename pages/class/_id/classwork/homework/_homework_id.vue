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
                <v-list-item-title>{{ item.title }}</v-list-item-title>
                <v-list-item-subtitle>{{
                  $moment(new Date(+item.created_at * 1000)).format(
                    'D MMM YYYY, h:mm'
                  )
                }}</v-list-item-subtitle>
              </v-list-item-content>
            </v-list-item>
          </v-card-title>

          <v-card-text v-if="item.description" class="font-weight-bold">
            {{ item.description }}
          </v-card-text>
          <v-card-text v-if="item.uploaded_file">
            <div class="d-flex">
              <v-card outlined>
                <div class="d-flex">
                  <v-avatar width="100" height="75" tile>
                    <v-icon x-large class="pt-2"> mdi-file </v-icon>
                  </v-avatar>
                  <div>
                    <v-card-title class="text-h6 pl-0">{{
                      item.uploaded_file.substring(
                        item.uploaded_file.lastIndexOf('/') + 1
                      )
                    }}</v-card-title>

                    <v-card-subtitle class="pl-0"
                      >{{ item.file_size }} MB</v-card-subtitle
                    >
                  </div>
                </div>
              </v-card>
            </div>
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
          <v-divider></v-divider>
          <v-card
            v-for="c in comments.results"
            :key="c.id"
            elevation="0"
            max-width="500"
          >
            <v-card-title>
              <v-list-item class="pl-0 grow">
                <v-list-item-avatar color="#10AFA7">
                  <img
                    v-if="c.author.avatar"
                    alt="Avatar"
                    :src="c.author.avatar"
                  />
                  <img
                    v-else
                    alt="Avatar"
                    src="https://avatars0.githubusercontent.com/u/9064066?v=4&s=460"
                  />
                </v-list-item-avatar>

                <v-list-item-content>
                  <v-list-item-title>
                    {{ c.author.first_name }} {{ c.author.last_name }}
                  </v-list-item-title>
                  <v-list-item-subtitle>
                    {{
                      $moment(new Date(+c.created_date * 1000)).format(
                        'D MMM YYYY, h:mm'
                      )
                    }}
                  </v-list-item-subtitle>
                </v-list-item-content>
              </v-list-item>
            </v-card-title>

            <v-card-text class="pb-0 font-weight-bold">
              {{ c.comment }}
            </v-card-text>
          </v-card>
          <v-card-actions class="pb-0">
            <v-form
              class="d-flex align-center justify-center"
              @submit.prevent="createComment"
            >
              <v-text-field
                v-model="comment"
                class="pt-4 px-3"
                label="Add comments"
              ></v-text-field>
              <v-btn
                color="#10AFA7"
                elevation="0"
                dark
                class="text-capitalize"
                type="submit"
                >Create comment</v-btn
              >
            </v-form>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  layout: 'classwork',
  middleware: ['auth'],
  async asyncData({ $axios, params }) {
    try {
      const item = await $axios.$get(
        `classes/classworkes/${params.homework_id}/`
      )
      const comments = await $axios.$get(
        `comments/classwork-class/${params.homework_id}/`
      )
      return { item, comments }
    } catch (err) {
      return { item: {} }
    }
  },
  data() {
    return {
      dialog: false,
      item: {},
      comment: '',
    }
  },
  methods: {
    async createComment() {
      try {
        await this.$axios.$post('comments/classwork-comment/', {
          comment: this.comment,
          classwork: this.$route.params.homework_id,
        })
        this.comments = await this.$axios.$get(
          `comments/classwork-class/${this.$route.params.homework_id}/`
        )
        this.comment = ''
      } catch (err) {
        // eslint-disable-next-line no-console
        console.log(err)
      }
    },
  },
}
</script>

<style scoped>
.v-input__slot {
  margin-bottom: 0;
}
</style>
