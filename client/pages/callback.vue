<template>
  <v-container>
    <v-row>
      <v-col cols="12" md="6">
        <div class="f-container">
          <h1 class="title">Logging you in...</h1>
          <div class="line"></div>
        </div>
      </v-col>
      <v-col cols="12" md="6">
        <img class="image animated" src="~/assets/logging_in.jpg" />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  created() {
    this.$auth.handleAuthentication()
  },
  methods: {
    handleLoginEvent(data) {
      this.$router.push(data.state.target || '/')
    }
  }
}
</script>

<style scoped>
.image {
  height: 100%;
  width: 100%;
  border-radius: 20px;
}

.title {
  font-weight: 100;
  font-size: 2.5rem !important;
  margin-bottom: 1rem;
}

.line {
  height: 5px;
  width: 50px;
  background: #674dfc;
  border-radius: 10px;
}

@keyframes floating {
  0% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(10px);
  }
  100% {
    transform: translateY(0px);
  }
}

.animated {
  animation: floating 3s ease infinite;
  will-change: transform;
}
</style>
