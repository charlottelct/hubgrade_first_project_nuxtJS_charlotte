<template>
  <v-app light>
      <v-toolbar color="primary" dark fixed app>
        <v-btn color="accent" home to="/"><v-icon>home</v-icon></v-btn>
        <v-toolbar-title>Welcome,</v-toolbar-title>
            <v-spacer></v-spacer><v-spacer></v-spacer>
                  <template v-if="$auth.$state.loggedIn">
              <v-btn color="accent" @click="logout">Logout</v-btn>
          </template>
          <template v-else>
            <v-btn color="accent" to="/login">Login</v-btn>
          </template>
      </v-toolbar>
    <v-content>
      <v-container grid-list-md text-xs-center>
          <v-layout row wrap>
          <v-flex xs12>
          </v-flex>
          </v-layout>
        <nuxt/>
      </v-container>
    </v-content>
      <v-footer color="primary" app inset>
      <span class="white--text"></span>
      <span>&copy; Coucou Nidrax</span>
    </v-footer>
  </v-app>
</template>

<script>
  export default {
    data () {
      return {
        clipped: false,
        fixed: false,
        miniVariant: false,
        right: true,
        title: 'Vuetify.js'
      }
    },
    methods: {
      logout () {
        this.$auth.logout()
      }
    }
}
</script>
