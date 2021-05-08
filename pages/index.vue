<template>
  <div>
    <v-row align="center" justify="center">
      <v-col cols="12">
        <SharedClassCardList />
      </v-col>
    </v-row>
    <div id="parent">
      <div class="mr-md-6"><SharedTeacher /></div>
      <div><PostCardList /></div>
    </div>
  </div>
</template>

<script>
import SharedClassCardList from '../components/classes/SharedClassCardList'
import PostCardList from '../components/posts/PostCardList'
import SharedTeacher from '../components/teachers/SharedTeacher'

export default {
  components: {
    SharedClassCardList,
    PostCardList,
    SharedTeacher,
  },
}
</script>

<style scoped>
#parent {
  display: grid;
  grid-template-columns: 1fr 4fr;
}
</style>
