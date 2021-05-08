<template>
  <Profile />
</template>

<script>
import Profile from '../../components/teachers/Profile'

export default {
  components: {
    Profile,
  },
  layout(context) {
    return 'detail'
  },
}
</script>
