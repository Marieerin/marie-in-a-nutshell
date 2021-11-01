<template>
  <div id="app" class="app" :class="mode" >
    <b-navbar toggleable="md" class="navBar" :variant="mode" :type="mode">
      <b-navbar-toggle target="nav_collapse"></b-navbar-toggle>
      <b-navbar-brand to="/">Marie in a nutshell</b-navbar-brand>
      <b-collapse is-nav id="nav_collapse">
        <b-navbar-nav>
          <b-nav-item to="/">Home</b-nav-item>
          <b-nav-item to="/posts-manager">Posts Manager</b-nav-item>
          <b-nav-item href="#" @click.prevent="login" v-if="!activeUser">Login</b-nav-item>
          <b-nav-item href="#" @click.prevent="logout" v-else>Logout</b-nav-item>
        </b-navbar-nav>
      </b-collapse>
      <Toggle :mode="mode" @toggle="toggle" />
    </b-navbar>
    <!-- routes will be rendered here -->
    <router-view />
  </div>
</template>

<style src="./styles.css"></style>

<script>
import Toggle from '@/components/Toggle'
export default {
  components: {
    Toggle
  },
  name: 'app',
  data () {
    return {
      activeUser: null,
      mode: 'dark'
    }
  },
  async created () {
    await this.refreshActiveUser()
  },
  watch: {
    // everytime a route is changed refresh the activeUser
    '$route': 'refreshActiveUser'
  },
  methods: {
    toggle () {
      // controls color mode functionality for Toggle.js component
      // - if move is dark change it to light else change to dark
      if (this.mode === "dark") {
        this.mode = "light"
      } else {
        this.mode = "dark"
      }
    },
    async login () {
      this.$auth.signInWithRedirect()
    },
    async refreshActiveUser () {
      if (this.authState.isAuthenticated) {
        this.activeUser = await this.$auth.getUser()
      }
    },
    async logout () {
      await this.$auth.signOut()
      await this.refreshActiveUser()
      this.$router.push('/')
    }
  }
}
</script>