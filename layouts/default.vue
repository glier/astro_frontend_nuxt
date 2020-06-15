<template>
  <v-app>
    <client-only>
      <v-navigation-drawer
        v-if="loggedIn"
        permanent
        expand-on-hover
        fixed
        app
      >
        <UserNavigation />
      </v-navigation-drawer>
    </client-only>
    <v-app-bar
      :clipped-left="clipped"
      flat
      app
    >
      <v-toolbar-title>
        <nuxt-link to="/">
          Astro
        </nuxt-link>
      </v-toolbar-title>
      <v-spacer />
      <v-spacer />
      <v-spacer />
      <v-spacer />
      <v-btn
        icon
        @click.stop="rightDrawer = !rightDrawer"
      >
        <v-icon>mdi-view-dashboard</v-icon>
      </v-btn>
      <v-btn
        icon
        @click.stop="rightDrawer = !rightDrawer"
      >
        <v-icon>mdi-bell</v-icon>
      </v-btn>
      <v-btn
        icon
        nuxt
        to="/login"
      >
        <v-icon>mdi-account</v-icon>
      </v-btn>
    </v-app-bar>
    <v-content>
      <nuxt />
    </v-content>
  <!--    <v-footer-->
  <!--      app-->
  <!--    >-->
  <!--      <span>&copy; {{ new Date().getFullYear() }}</span>-->
  <!--    </v-footer>-->
  </v-app>
</template>

<script>
import { mapState } from 'vuex'
import UserNavigation from '../components/navigation/UserNavigation'

export default {
  components: { UserNavigation },
  data () {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Inspire',
          to: '/inspire'
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Vuetify.js',
      itemsSearch: [],
      search: null,
      select: null
    }
  },
  computed: {
    ...mapState('auth', ['loggedIn', 'user'])
  }
}
</script>

<style scoped>

</style>
