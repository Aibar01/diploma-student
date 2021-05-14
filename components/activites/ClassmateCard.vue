<template>
  <v-card outlined class="ml-lg-12 ml-sm-0 mt-10" max-width="170">
    <v-img
      v-if="user.avatar"
      class="white--text align-end"
      height="170px"
      :src="user.avatar"
    />
    <v-img
      v-else
      class="white--text align-end"
      height="170px"
      src="https://aardvark.ghostpool.com/original/wp-content/uploads/avatars/72/5cbddabff083e-bpfull.jpg"
    />

    <v-card-title class="pb-0 subtitle-2">
      {{ user.first_name }} {{ user.last_name }}
    </v-card-title>
    <v-card-subtitle v-if="user.role_type === 'teacher'" class="pt-4 caption">
      Мұғалім
    </v-card-subtitle>
    <v-card-subtitle v-else class="pt-4 caption"> Студент </v-card-subtitle>
  </v-card>
</template>

<script>
export default {
  props: {
    user: {
      type: Object,
      required: true,
    },
  },
}
</script>
