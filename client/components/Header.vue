<template>
  <v-toolbar>
    <v-toolbar-title>
      <img class="icon" src="~/assets/icon.png" />
    </v-toolbar-title>
    <div class="flex-grow-1"></div>

    <v-toolbar-items>
      <v-btn v-if="!isAuthenticated" text @click="login">Login</v-btn>
      <v-btn v-else text @click="logout">Logout</v-btn>
    </v-toolbar-items>
  </v-toolbar>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      isAuthenticated: false
    }
  },
  async created() {
    try {
      await this.$auth.renewTokens()
    } catch (e) {
      console.log(e)
    }
  },
  methods: {
    login() {
      this.$auth.login()
    },
    logout() {
      this.$auth.logOut()
    },
    handleLoginEvent(data) {
      this.isAuthenticated = data.loggedIn
    }
  }
}
</script>

<style scoped>
.icon {
  width: 40px;
  height: 40px;
}

.links {
  margin-left: auto;
}
</style>
