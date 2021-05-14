<template>
  <v-app dark>
    <v-app-bar
      absolute
      color="white"
      flat
      elevate-on-scroll
      scroll-target="#scrolling-techniques-7"
      class="app"
      outlined
      elevation="0"
    >
      <v-toolbar-title class="font-weight-bold">LOGO</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>
    </v-app-bar>
    <v-main class="mt-10">
      <nuxt />
    </v-main>
    <v-footer :absolute="!fixed" app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      clipped: false,
      drawer: true,
      fixed: true,
      items: [
        { title: 'Feed', icon: 'mdi-view-dashboard' },
        { title: 'Notifications', icon: 'mdi-image' },
      ],
      miniVariant: false,
      right: true,
      title: 'Diploma',
    }
  },
}
</script>

<style>
* {
  font-family: 'Rubik', sans-serif;
}

.v-input--selection-controls .v-input__control {
  width: 100%;
}
.v-tab {
  color: #353232;
}
.v-application .primary--text {
  color: #353232 !important;
  caret-color: #353232 !important;
}

.app {
  padding-left: 10%;
  padding-right: 10%;
}

a {
  text-decoration: none;
  color: black !important;
}

img {
  object-fit: cover;
}
</style>
