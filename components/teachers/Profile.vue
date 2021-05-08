<template>
  <div>
    <v-card>
      <v-img
        max-height="224"
        src="https://coolbackgrounds.io/images/backgrounds/index/sea-edge-79ab30e2.png"
      >
      </v-img>
    </v-card>
    <v-container>
      <v-row>
        <v-col cols="2">
          <v-card
            d-flex
            justify="center"
            align="center"
            class="mx-auto my-12"
            max-width="374"
            elevation="0"
            style="position: absolute; left: 100px; top: 70px"
          >
            <div id="avatar" class="pt-10 px-10">
              <v-avatar size="120">
                <img
                  alt="user"
                  src="https://img.freepik.com/free-photo/handsome-young-businessman-in-shirt-and-eyeglasses_85574-6228.jpg?size=626&ext=jpg"
                />
              </v-avatar>
              <v-card-subtitle class="title black--text pb-0"
                >Айбар Беккожаев</v-card-subtitle
              >
              <v-card-subtitle class="pt-2"
                >Programming мұғалым</v-card-subtitle
              >
            </div>
          </v-card>
        </v-col>
        <v-col cols="10">
          <TeacherProfileClassPreview />
        </v-col>
      </v-row>
      <v-row>
        <v-col>
          <TeacherSharedList />
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import TeacherProfileClassPreview from '../../components/teachers/TeacherProfileClassPreview'
import TeacherSharedList from '../../components/teachers/TeacherSharedList'
export default {
  components: {
    TeacherProfileClassPreview,
    TeacherSharedList,
  },
}
</script>

<style scoped>
.v-main__wrap {
  background-color: #efeeee;
}
</style>
