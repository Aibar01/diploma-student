<template>
  <v-card class="pl-5 pt-5" elevation="0" max-width="700">
    <v-row>
      <v-col class="font-weight-bold text-uppercase">General</v-col>
      <v-col>5 videos</v-col>
    </v-row>
    <v-row>
      <v-col class="font-weight-bold text-uppercase">About course</v-col>
      <v-col> {{ teacherClass.about_course }} </v-col>
    </v-row>
    <v-row>
      <v-col class="font-weight-bold text-uppercase">Syllabus</v-col>
      <v-col class="d-flex"
        ><div v-for="prop in teacherClass.syllabus" :key="prop">
          {{ prop + ', ' }}
        </div>
      </v-col>
    </v-row>
    <v-row>
      <v-col class="font-weight-bold text-uppercase">Teacher</v-col>
      <v-col>
        <v-card elevation="0" max-width="800">
          <v-card-title class="pt-0">
            <v-list-item class="pl-0 grow">
              <v-list-item-avatar color="#10AFA7">
                <img
                  v-if="teacherClass.teacher.avatar"
                  alt="Avatar"
                  :src="teacherClass.teacher.avatar"
                />
                <img
                  v-else
                  alt="Avatar"
                  src="https://avatars0.githubusercontent.com/u/9064066?v=4&s=460"
                />
              </v-list-item-avatar>

              <v-list-item-content>
                <v-list-item-title>
                  {{ teacherClass.teacher.first_name }}
                  {{ teacherClass.teacher.last_name }}
                </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-card-title>
        </v-card>
      </v-col>
    </v-row>
  </v-card>
</template>

<script>
export default {
  layout: 'class',
  async asyncData({ $axios, params }) {
    try {
      const teacherClass = await $axios.$get(`classes/class/${params.id}/`)
      return {
        teacherClass,
      }
    } catch (err) {
      return { teacherClass: {} }
    }
  },
}
</script>
