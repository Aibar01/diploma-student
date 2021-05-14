<template>
  <v-card elevation="0" class="my-10" max-width="1000">
    <v-card-title>
      <strong> {{ item.title }} </strong>
    </v-card-title>

    <v-card-subtitle class="pt-4 pb-6">
      <v-icon small class="pb-1"> mdi-calendar-blank-outline </v-icon>
      {{ $moment(new Date(+item.created_date * 1000)).format('MMM D, YYYY') }}
    </v-card-subtitle>
    <v-img
      v-if="item.main_image"
      class="white--text align-end"
      max-height="420px"
      max-width="100%"
      :src="item.main_image"
    />
    <v-img
      v-else
      class="white--text align-end"
      max-height="420px"
      max-width="100%"
      src="https://keystoneacademic-res.cloudinary.com/image/upload/f_auto,q_auto,c_fill,w_1920/element/13/132557_UnicafHL.jpg"
    />

    <v-card-text class="text--primary">
      <div>
        {{ item.text }}
      </div>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  data() {
    return {
      item: {},
    }
  },
  async fetch() {
    this.item = await this.$axios.$get(`news/news/${this.$route.params.id}/`)
  },
}
</script>
