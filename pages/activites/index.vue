<template>
  <div>
    <NoActivites v-if="noActivites" />
    <div v-else>
      <ClassmatePostList v-for="item in items" :key="item" />
    </div>
  </div>
</template>

<script>
import NoActivites from '../../components/activites/NoActivites'
import ClassmatePostList from '../../components/activites/ClassmatePostList'

export default {
  components: {
    NoActivites,
    ClassmatePostList,
  },
  data() {
    return {
      noActivites: false,
      items: [1, 2, 3, 4],
    }
  },
}
</script>
