<template>
  <div>
    <v-card>
      <v-img
        v-if="$auth.user.cover_image"
        max-height="258"
        :src="$auth.user.cover_image"
      />
      <v-img
        v-else
        max-height="258"
        src="https://coolbackgrounds.io/images/backgrounds/index/sea-edge-79ab30e2.png"
      />
    </v-card>
    <v-container>
      <v-row>
        <v-col cols="2">
          <v-card
            d-flex
            justify="center"
            align="center"
            class="mx-auto my-12"
            max-width="258"
            elevation="0"
            style="position: absolute; left: 100px; top: 70px"
          >
            <div id="avatar" class="pt-10 px-10">
              <v-avatar size="120">
                <img
                  v-if="$auth.user.avatar"
                  alt="user"
                  :src="$auth.user.avatar"
                />
                <img
                  v-else
                  alt="user"
                  src="https://img.freepik.com/free-photo/handsome-young-businessman-in-shirt-and-eyeglasses_85574-6228.jpg?size=626&ext=jpg"
                />
              </v-avatar>
              <v-card-subtitle class="title black--text pb-0"
                >{{ $auth.user.first_name }}
                {{ $auth.user.last_name }}</v-card-subtitle
              >
              <v-card-subtitle class="pt-2">Студент</v-card-subtitle>
              <v-divider></v-divider>
              <v-card-text d-flex align="start">
                {{ $auth.user.bio }}
              </v-card-text>
              <v-card-text d-flex align="center">
                <v-btn
                  to="profile/settings"
                  color="#10AFA7"
                  style="color: #10afa7 !important"
                  class="text-capitalize"
                  text
                >
                  <strong> Edit Profile </strong>
                </v-btn>
              </v-card-text>
            </div>
          </v-card>
        </v-col>
        <v-col cols="10">
          <StudentClassesCard />
        </v-col>
      </v-row>
      <v-row>
        <v-col>
          <StudentResultCard />
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import StudentClassesCard from './StudentClassesCard'
import StudentResultCard from './StudentResultCard'

export default {
  components: {
    StudentResultCard,
    StudentClassesCard,
  },
}
</script>

<style scoped>
.v-main__wrap {
  background-color: #efeeee;
}
</style>
