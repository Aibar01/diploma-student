<template>
  <div>
    <v-row align="center" justify="center">
      <v-col cols="12">
        <SharedClassCardList :classes="classes" />
      </v-col>
    </v-row>
    <div id="parent">
      <ClassmatePostList :news="news.results" />
    </div>
  </div>
</template>

<script>
import SharedClassCardList from '../components/classes/SharedClassCardList'
import ClassmatePostList from '../components/activites/ClassmatePostList'

export default {
  components: {
    SharedClassCardList,
    ClassmatePostList,
  },
  async asyncData({ $axios }) {
    try {
      const news = await $axios.$get('/news/news')
      const classes = await $axios.$get('classes/student-not/')
      return { news, classes }
    } catch (err) {
      return { news: [], classes: [] }
    }
  },
  data() {
    return {
      news: [],
      classes: [],
    }
  },
}
</script>

<style scoped>
#parent {
  display: grid;
  grid-template-columns: 1fr 4fr;
}
</style>
