<template>
  <v-app dark>
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
    >
      <v-list-item class="py-2">
        <v-list-item-content>
          <v-list-item-title class="d-flex align-center">
            <nuxt-link color="#fff" :to="`/class/${$route.params.id}/classwork`"
              ><v-icon>mdi-arrow-left</v-icon> Артқа</nuxt-link
            >
          </v-list-item-title>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list dense nav>
        <v-list-item v-for="item in items" :key="item.title" link>
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <NuxtLink :to="item.to">
              <v-list-item-title>{{ item.title }}</v-list-item-title>
            </NuxtLink>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar
      :clipped-left="clipped"
      fixed
      app
      outlined
      elevation="0"
      color="#fff"
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />

      <v-toolbar-title class="font-weight-bold">Толығырақ</v-toolbar-title>
    </v-app-bar>
    <v-main>
      <nuxt />
    </v-main>
    <v-footer :absolute="!fixed" app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  middleware: ['auth'],
  data() {
    return {
      clipped: false,
      drawer: true,
      fixed: true,
      items: [],
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

/* .v-text-field > .v-input__control > .v-input__slot:before {
  border-color: transparent !important;
}
.v-text-field > .v-input__control > .v-input__slot:hover {
  border-color: transparent !important;
} */

a {
  text-decoration: none;
  color: #353232 !important;
}
</style>
