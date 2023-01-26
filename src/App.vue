<template>
  <div v-if="loading" class="loader">Loading...</div>
  <div class="main">
    <img class="hello" alt="Vue logo" src="./assets/logo.png" />
    <ColorApp
      msg="Welcome to Your Vue.js App"
      v-on:loadingCheck="updateLoading()"
    />
  </div>
</template>

<script>
import ColorApp from "./components/ColorApp.vue";

export default {
  name: "App",
  components: {
    ColorApp,
  },
  data: function () {
    return {
      loading: true,
      updateLoading: function () {
        this.loading = false;
      },
    };
  },
};
</script>

<style>
#app,
html,
body {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0;
  padding: 0;
  height: 100%;
}

.hello {
  margin-top: 50px;
}

.loader {
  color: white;
  position: absolute;
  height: 100vh;
  width: 100vw;
  background: rgba(0, 0, 0, 0.3);
  font-size: 30px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}
</style>
