<template>
  <div class="parent">
    <PostCard v-for="item in items" :key="item" />
  </div>
</template>

<script>
import PostCard from './PostCard'

export default {
  components: {
    PostCard,
  },
  data() {
    return {
      items: [1, 2, 3],
    }
  },
}
</script>

<style scoped>
.parent {
  display: grid;
}
</style>
