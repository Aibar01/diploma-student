<template>
  <div class="pl-5">
    <v-card class="pb-5" elevation="0" max-width="900">
      <v-card-title class="pb-0"> </v-card-title>
    </v-card>
    <v-card
      v-for="i in classworks.results"
      :key="i.id"
      outlined
      max-width="500"
      class="mt-8"
    >
      <v-card-title>
        <v-list-item class="pl-0 grow">
          <nuxt-link :to="`${i.classwork_type}/${i.id}/`">
            <v-list-item-avatar color="#10AFA7">
              <span class="white--text headline">
                <v-icon dark>mdi-notebook</v-icon>
              </span>
            </v-list-item-avatar>
          </nuxt-link>
          <v-list-item-content>
            <div class="d-flex">
              <nuxt-link :to="`classwork/${i.classwork_type}/${i.id}`">
                <div>
                  <v-list-item-title>{{ i.title }}</v-list-item-title>
                  <v-list-item-subtitle>{{
                    $moment(new Date(+i.created_at * 1000)).format(
                      'D MMM YYYY, h:mm'
                    )
                  }}</v-list-item-subtitle>
                </div>
              </nuxt-link>
            </div>
          </v-list-item-content>
        </v-list-item>
      </v-card-title>
      <v-card-text v-if="i.description" class="font-weight-bold">
        {{ i.description }}
      </v-card-text>
      <v-card-text v-if="i.due_date" class="font-weight-bold">
        Due to
        {{ $moment(new Date(+i.due_date * 1000)).format('D MMM YYYY, h:mm') }}
      </v-card-text>
    </v-card>
  </div>
</template>

<script>
export default {
  layout: 'class',
  middleware: 'auth',
  async asyncData({ $axios, params }) {
    try {
      const classworks = await $axios.$get(`classes/classworkes/`, {
        params: { class: params.id },
      })
      return {
        classworks,
      }
    } catch (err) {
      return { classworks: [] }
    }
  },
  data() {
    return {
      editClasswork: {
        title: '',
        description: '',
        uploaded_file: null,
      },
      dialog: false,
      editDialog: false,
      editMenu: false,
      closeOn: true,
      classworks: [],
      date: '',
      time: '',
      menu: false,
      menu2: false,
      items: [
        { title: 'Lesson', icon: 'mdi-circle' },
        { title: 'Homework', icon: 'mdi-circle' },
        { title: 'Material', icon: 'mdi-circle' },
      ],
    }
  },
  methods: {
    async getItems() {
      try {
        this.classworks = await this.$axios.$get(`classes/classworkes/`, {
          params: { class: this.$route.params.id },
        })
      } catch (err) {
        // eslint-disable-next-line no-console
        console.log(err)
      }
    },
  },
}
</script>
