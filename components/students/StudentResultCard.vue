<template>
  <v-card elevation="0" max-width="975" class="ml-auto ml-lg-auto mt-5">
    <v-container>
      <v-row>
        <v-col v-for="(item, i) in items" :key="i" cols="12">
          <v-card elevation="0" class="mt-10" max-width="1000">
            <v-img
              class="white--text align-end"
              max-height="420px"
              max-width="100%"
              src="https://keystoneacademic-res.cloudinary.com/image/upload/f_auto,q_auto,c_fill,w_1920/element/13/132557_UnicafHL.jpg"
            >
            </v-img>

            <v-card-subtitle class="pb-0">
              <v-icon small class="pb-1"> mdi-calendar-blank-outline </v-icon>
              Sep 8, 2020
            </v-card-subtitle>

            <v-card-title>
              <strong> You got 97% points on your first quiz! </strong>
            </v-card-title>

            <v-card-text class="text--primary">
              <div>
                Congratulations! You’ve did a great job! Keep going and learn
                more with us.
              </div>
            </v-card-text>

            <v-card-actions>
              <v-btn color="black" class="text-lowercase" text>
                hide from everyone
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </v-card>
</template>

<script>
export default {
  data: () => ({
    items: [
      {
        src: 'https://cdn.vuetifyjs.com/images/cards/foster.jpg',
        title: 'Here will be One lined Post title 2021',
        teacher: 'Jane Smith',
      },
      {
        src: 'https://cdn.vuetifyjs.com/images/cards/halcyon.png',
        title: 'Here will be One lined Post title 2021',
        teacher: 'Jane Smith',
      },
    ],
  }),
}
</script>
