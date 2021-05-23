<template>
  <v-card elevation="0" class="mt-10" max-width="1000">
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
    <v-card-subtitle class="pb-0">
      <v-icon small class="pb-1"> mdi-calendar-blank-outline </v-icon>
      {{ $moment(new Date(+item.created_date * 1000)).format('MMM D, YYYY') }}
    </v-card-subtitle>

    <v-card-title>
      <strong> {{ item.title }} </strong>
    </v-card-title>

    <v-card-text class="text--primary">
      <div>{{ item.text.split('.')[0] }}...</div>
    </v-card-text>

    <v-card-actions>
      <v-btn color="black" class="text-capitalize" text>
        <NuxtLink :to="`/activites/${1}`">
          <strong> Толығырақ оқу </strong>
        </NuxtLink>
      </v-btn>
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
}
</script>

<style scoped>
a {
  text-decoration: none;
  color: #10afa7 !important;
}
</style>
