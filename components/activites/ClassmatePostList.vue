<template>
  <div>
    <div v-for="item in news" id="parent" :key="item.id">
      <div class="mr-md-6"><ClassmateCard :user="item.author" /></div>
      <div><ClassmatePostCard :item="item" /></div>
    </div>
  </div>
</template>

<script>
import ClassmateCard from './ClassmateCard'
import ClassmatePostCard from './ClassmatePostCard'

export default {
  components: {
    ClassmatePostCard,
    ClassmateCard,
  },
  props: {
    news: {
      type: Array,
      required: true,
    },
  },
}
</script>

<style scoped>
#parent {
  display: grid;
  grid-template-columns: 1fr 4fr;
}
</style>
