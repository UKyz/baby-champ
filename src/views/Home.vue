<template>
  <v-app id="inspire">
    <v-navigation-drawer
      v-model="drawer"
      app
      clipped
    >
      <v-list dense>
        <v-list-item link @click="changePage('rank')">
          <v-list-item-action>
            <v-icon>mdi-chevron-triple-up</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Classement</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item link @click="changePage('game')">
          <v-list-item-action>
            <v-icon>mdi-plus-circle-outline</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Ajouter un match</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar
      app
      clipped-left
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-toolbar-title>Baby Championnat</v-toolbar-title>
    </v-app-bar>

    <v-content>
      <rank v-if="page === 'rank'"/>
      <match v-else-if="page === 'game'"/>
    </v-content>

    <v-footer app>
      <span>&copy; Scalair - Championnat Baby - 2020</span>
    </v-footer>
  </v-app>
</template>

<script>
// @ is an alias to /src
import Match from '@/components/Match.vue'
import Rank from '@/components/Rank.vue'

export default {
  name: 'Home',
  components: {
    Match,
    Rank
  },
  props: {
    source: String
  },
  data: () => ({
    drawer: false,
    page: 'rank'
  }),
  created () {
    this.$vuetify.theme.dark = true
  },
  methods: {
    changePage (page) {
      this.page = page
      this.drawer = false
    }
  }
}
</script>
