<template>
  <v-app light>
    <v-content>
      <v-container grid-list-md text-xs-center>
          <v-layout row wrap>
          <v-flex xs12>
          <v-card dark color="primary">
          <v-card-text class="px-0">Bienvenue beauté des îles</v-card-text>
          </v-card>
          </v-flex>
          </v-layout>
        <nuxt/>
      </v-container>
    </v-content>
    <v-footer :fixed="fixed" app>
      <v-btn color="info" home to="/"><v-icon>home</v-icon></v-btn>
      <span>&copy; Coucou Nidrax</span>
    </v-footer>
  </v-app>
</template>

<script>
  export default {
    data () {
      return {
        clipped: false,
        drawer: false,
        fixed: false,
        items: [
          { icon: 'apps', title: 'Welcome', to: '/' },
          { icon: 'bubble_chart', title: 'Inspire', to: '/inspire' }
        ],
        miniVariant: false,
        right: true,
        rightDrawer: false,
        title: 'Vuetify.js'
      }
    }
  }
</script>
