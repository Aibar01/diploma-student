<template>
  <Profile />
</template>

<script>
import Profile from '../../../components/students/Profile'

export default {
  components: {
    Profile,
  },
  layout(context) {
    return 'detail'
  },
}
</script>
