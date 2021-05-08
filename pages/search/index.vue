<template>
  <div>
    <h1>Search results for <b>“Scratch”</b></h1>

    <SharedClassCardList />

    <SearchResultList />
  </div>
</template>

<script>
import SharedClassCardList from '../../components/classes/SharedClassCardList'
import SearchResultList from '../../components/search/SearchResultList'

export default {
  components: {
    SharedClassCardList,
    SearchResultList,
  },
}
</script>
