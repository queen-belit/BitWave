<template>
  <v-app :dark="dark">

    <!-- Toolbar -->
    <v-toolbar
      :clipped-left="clipped"
      clipped-right
      flat
      dark
      dense
      fixed
      app
    >
      <!--<v-toolbar-side-icon @click="drawer = !drawer">
        <v-icon large>devices</v-icon>
      </v-toolbar-side-icon>-->

      <!--<v-toolbar-side-icon @click="drawer = !drawer" />-->

      <v-toolbar-title class="ml-0 mr-1">
        <v-btn
          to="/"
          depressed
          flat
          exact
          active-class
          class="text-none title px-2"
        >{{ title }}</v-btn>
      </v-toolbar-title>

      <v-spacer />

      <user/>

      <!--<v-btn
        v-show="mobile"
        :class="{ 'mr-2': mobile }"
        icon
        @click.stop="showChat = !showChat"
      >
        <v-icon>menu</v-icon>
      </v-btn>-->

    </v-toolbar>

    <!-- R-Nav Chat Drawer -->
    <!--<v-navigation-drawer
      v-model="showChat"
      :width="width"
      :permanent="$vuetify.breakpoint.mdAndUp"
      right
      clipped
      fixed
      flat
      app
    >
      <chat :dark="dark" />
    </v-navigation-drawer>-->

    <!-- L-Nav Drawer -->
    <user-list />

    <!-- Content -->
    <v-content>
      <nuxt />
    </v-content>

  </v-app>
</template>

<script>
  import User from '~/components/User'
  import UserList from '~/components/UserList'

  import { mapState } from 'vuex'

  export default {
    components: {
      User,
      UserList,
    },

    data() {
      return {
        title: '[bitwave.tv]',

        dark: true,
        clipped: false,
        fixed: false,

        miniVariant: true,
        drawer: true,

        right: true,
        showChat: true,
      }
    },

    methods: {

    },

    computed: {
      ...mapState({
        currentUser: state => state.user.currentUser,
      }),

      mobile () {
        return !this.$vuetify.breakpoint.mdAndUp;
      },

      width () {
        return this.$vuetify.breakpoint.smAndUp ? 450 : 300;
      },
    },

    created() {
      this.showChat = this.$vuetify.breakpoint.smAndUp;
    }
  }
</script>

<style>
  /*.v-toolbar__content {
    padding-left: 0;
    padding-right: 0;
  }*/
</style>
