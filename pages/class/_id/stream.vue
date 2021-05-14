<template>
  <div class="mt-10 pl-5">
    <v-card v-if="Boolean(items.length)" max-width="500" outlined>
      <v-card-text>
        <p class="headline text--primary">Communicate with your students</p>
        <p>
          <v-icon class="pr-2" color="black" x-small>mdi-circle</v-icon>Create
          and schedule announcements
        </p>
        <p>
          <v-icon class="pr-2" color="black" x-small>mdi-circle</v-icon>Respond
          to student posts
        </p>
      </v-card-text>
    </v-card>

    <v-card
      v-for="item in items.results"
      :key="item.id"
      outlined
      max-width="500"
      class="mt-8"
    >
      <v-card-title>
        <v-list-item class="pl-0 grow">
          <v-list-item-avatar>
            <img
              v-if="$auth.user.avatar"
              alt="Avatar"
              :src="$auth.user.avatar"
            />
            <img
              v-else
              alt="Avatar"
              src="https://avatars0.githubusercontent.com/u/9064066?v=4&s=460"
            />
          </v-list-item-avatar>

          <v-list-item-content>
            <div class="d-flex">
              <div>
                <v-list-item-title
                  >{{ $auth.user.first_name }}
                  {{ $auth.user.last_name }}</v-list-item-title
                >
                <v-list-item-subtitle
                  >12 Mar 2021 at 12:01</v-list-item-subtitle
                >
              </div>
            </div>
          </v-list-item-content>
        </v-list-item>
      </v-card-title>

      <v-card-text class="font-weight-bold">
        {{ item.annoucment_text }}
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
      const items = await $axios.$get(`classes/announcment/`, {
        params: { class: params.id },
      })
      return { items }
    } catch (e) {
      return { items: [] }
    }
  },
  data() {
    return {
      items: [],
    }
  },
}
</script>
