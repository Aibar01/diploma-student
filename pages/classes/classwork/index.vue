<template>
  <v-container fluid>
    <v-row class="pt-5 pl-5">
      <v-col v-for="(item, index) in data" :key="index" cols="12">
        <v-card outlined max-width="500">
          <v-card-title class="py-0">
            <v-list-item class="pl-0 pr-0 grow">
              <v-list-item-avatar color="#10AFA7">
                <span class="white--text headline">
                  <v-icon dark>mdi-notebook</v-icon>
                </span>
              </v-list-item-avatar>

              <v-list-item-content>
                <div style="display: flex">
                  <v-list-item-title>{{ item.title }}</v-list-item-title>
                  <v-btn icon color="#C4C4C4">
                    <v-icon>mdi-dots-horizontal</v-icon>
                  </v-btn>
                </div>
                <v-list-item-subtitle>{{ item.date }}</v-list-item-subtitle>
              </v-list-item-content>
            </v-list-item>
          </v-card-title>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  layout(context) {
    return 'blog'
  },
  data() {
    return {
      data: [
        {
          title: 'Homework 1: Create character',
          content:
            'Try to make your own character in the Scratch by the methods that we learned in Lesson 1. No cheating!!!',
          date: '12 Mar 2021 at 12:01',
          type: 'homework',
        },
        {
          title: 'Lesson 1: Introduction to Scratch',
          content: 'This lesson introduces you the basics of Scratch platform',
          date: '12 Mar 2021 at 12:01',
          type: 'lesson',
        },
        {
          title: 'Announcement: Welcome to Everyone!',
          content:
            'Hello everyone! I am glad to welcome you to this course based on Scratch. I am adding every student mannually, if you have friends who didn’t join this class till 18.03.2021 ask them to email me directly. Thank you!',
          date: '12 Mar 2021 at 12:01',
          type: 'notfication',
        },
      ],
    }
  },
}
</script>
