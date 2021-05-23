<template>
  <v-app dark>
    <div>
      <v-alert
        :value="alert"
        type="success"
        dark
        border="top"
        icon="mdi-home"
        transition="scale-transition"
      >
        success
      </v-alert>
    </div>
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
    >
      <v-list-item class="py-2">
        <v-list-item-content v-if="$auth.loggedIn">
          <nuxt-link to="/profile"
            ><v-list-item-title>{{
              $auth.user.email
            }}</v-list-item-title></nuxt-link
          >
        </v-list-item-content>
        <v-list-item-content v-else>
          <v-list-item-title>Профиль</v-list-item-title>
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
        <template v-if="$auth.loggedIn">
          <v-list-item v-for="item in classes.results" :key="item.id" link>
            <v-list-item-icon>
              <v-icon>mdi-google-classroom</v-icon>
            </v-list-item-icon>

            <v-list-item-content>
              <NuxtLink :to="`/class/${item.id}/stream`">
                <v-list-item-title>{{ item.class_name }}</v-list-item-title>
              </NuxtLink>
            </v-list-item-content>
          </v-list-item>
        </template>
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
      <v-tabs>
        <v-tabs-slider color="#353232"></v-tabs-slider>
        <v-tab class="text-capitalize">Сынып іздеңіз...</v-tab>
        <!-- <v-tab class="text-capitalize">Students Activity</v-tab> -->
      </v-tabs>
      <v-spacer />
      <v-text-field
        class="pt-4 pr-6"
        label="Search classes, teachers"
        prepend-icon="mdi-magnify"
      ></v-text-field>

      <v-dialog
        v-if="!$auth.loggedIn"
        v-model="dialog"
        persistent
        max-width="600px"
      >
        <template #activator="{ on, attrs }">
          <v-btn v-bind="attrs" v-on="on"> Register </v-btn>
        </template>
        <v-card>
          <v-form @submit.prevent="registerUser">
            <v-card-title>
              <span class="headline">User Profile</span>
            </v-card-title>
            <v-card-text>
              <v-container>
                <v-row>
                  <v-col cols="12" sm="6" md="6">
                    <v-text-field
                      v-model="user.first_name"
                      label="Legal first name*"
                      required
                    ></v-text-field>
                  </v-col>
                  <v-col cols="12" sm="6" md="6">
                    <v-text-field
                      v-model="user.last_name"
                      label="Legal last name*"
                      hint="example of persistent helper text"
                      persistent-hint
                      required
                    ></v-text-field>
                  </v-col>
                  <v-col cols="12">
                    <v-text-field
                      v-model="user.email"
                      label="Email*"
                      required
                    ></v-text-field>
                  </v-col>
                  <v-col cols="12">
                    <v-text-field
                      v-model="user.password"
                      label="Password*"
                      type="password"
                      required
                    ></v-text-field>
                  </v-col>
                  <v-col cols="12">
                    <v-text-field
                      v-model="user.confirm_password"
                      label="Confirm password*"
                      type="password"
                      required
                    ></v-text-field>
                  </v-col>
                </v-row>
              </v-container>

              <small>*indicates required field</small>
            </v-card-text>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn color="#10AFA7" text @click="dialog = false">
                Close
              </v-btn>
              <v-btn color="#10AFA7" text type="submit"> Register </v-btn>
            </v-card-actions>
          </v-form>
        </v-card>
      </v-dialog>

      <v-dialog
        v-if="!$auth.loggedIn"
        v-model="loginDialog"
        persistent
        max-width="600px"
      >
        <template #activator="{ on, attrs }">
          <v-btn v-bind="attrs" v-on="on"> Login </v-btn>
        </template>
        <v-card>
          <v-form @submit.prevent="loginUser">
            <v-card-title>
              <span class="headline">User Login</span>
            </v-card-title>
            <v-card-text>
              <v-container>
                <v-row>
                  <v-col cols="12">
                    <v-text-field
                      v-model="login.email"
                      label="Email*"
                      required
                    ></v-text-field>
                  </v-col>
                  <v-col cols="12">
                    <v-text-field
                      v-model="login.password"
                      label="Password*"
                      type="password"
                      required
                    ></v-text-field>
                  </v-col>
                </v-row>
              </v-container>

              <small>*indicates required field</small>
            </v-card-text>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn color="#10AFA7" text @click="loginDialog = false">
                Close
              </v-btn>
              <v-btn color="#10AFA7" text type="submit"> Login </v-btn>
            </v-card-actions>
          </v-form>
        </v-card>
      </v-dialog>
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
  data() {
    return {
      classes: [],
      dialog: false,
      classDialog: false,
      loginDialog: false,
      clipped: false,
      drawer: true,
      fixed: true,
      items: [
        {
          title: 'Басты бет',
          icon: 'mdi-view-dashboard',
          to: '/',
        },
        {
          title: 'Хабарлама',
          icon: 'mdi-bell',
          to: '/notification',
        },
        {
          title: 'Көмек',
          icon: 'mdi-information',
          to: '/settings/about',
        },
      ],
      miniVariant: false,
      right: true,
      title: 'Diploma',
      alert: false,
      user: {
        first_name: '',
        last_name: '',
        email: '',
        password: '',
        confirm: '',
        role_type: 'student',
      },
      login: {
        email: '',
        password: '',
      },
    }
  },
  async fetch() {
    try {
      this.classes = await this.$axios.$get('classes/student-classes/')
    } catch (err) {
      // eslint-disable-next-line no-console
      console.log(err)
    }
  },
  methods: {
    async registerUser() {
      try {
        const response = await this.$axios.$post('accounts/register/', {
          ...this.user,
        })
        // eslint-disable-next-line no-console
        console.log(response)
      } catch (err) {
        // eslint-disable-next-line no-console
        console.log(err)
      }

      this.dialog = false

      this.alert = true

      this.user = {
        first_name: '',
        last_name: '',
        email: '',
        password: '',
        confirm: '',
        role_type: 'teacher',
      }
    },
    async loginUser() {
      try {
        const response = await this.$auth.loginWith('local', {
          data: this.login,
        })
        if (this.$auth.user.role_type === 'teacher') {
          await this.$auth.logout()
        }
        // eslint-disable-next-line no-console
        console.log(response.access)
      } catch (err) {
        // eslint-disable-next-line no-console
        console.log(err)
      }

      this.loginDialog = false
      this.login = {
        email: '',
        password: '',
      }
    },
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
  color: #10afa7;
}
.v-application .primary--text {
  color: #10afa7 !important;
  caret-color: #10afa7 !important;
}

img {
  object-fit: cover;
}

/* .v-text-field > .v-input__control > .v-input__slot:before {
  border-color: transparent !important;
}
.v-text-field > .v-input__control > .v-input__slot:hover {
  border-color: transparent !important;
} */
</style>
