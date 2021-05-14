<template>
  <div>
    <v-container class="mt-5">
      <v-row>
        <v-col>
          <div>
            <NuxtLink to="/" prefetch class="d-flex align-center">
              <v-icon>mdi-arrow-left</v-icon>
              <div class="text-capitalize font-weight-bold">Back to Main</div>
            </NuxtLink>
          </div>
        </v-col>
      </v-row>
    </v-container>
    <div class="d-flex justify-center">
      <ClassmatePostDetail />
    </div>
  </div>
</template>

<script>
import ClassmatePostDetail from '../../../components/activites/ClassmatePostDetail'
export default {
  components: {
    ClassmatePostDetail,
  },
  layout(context) {
    return 'detail'
  },
}
</script>
