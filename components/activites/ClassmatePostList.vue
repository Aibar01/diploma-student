<template>
  <div>
    <div id="parent">
      <div class="mr-md-6"><ClassmateCard /></div>
      <div><ClassmatePostCard /></div>
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
}
</script>

<style scoped>
#parent {
  display: grid;
  grid-template-columns: 1fr 4fr;
}
</style>
