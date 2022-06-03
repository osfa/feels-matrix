<template>
  <div id="app">
    <FeelsViewer />
  </div>
</template>

<script>
import FeelsViewer from "./components/FeelsViewer.vue";

export default {
  name: "App",
  components: {
    FeelsViewer,
  },
};
</script>

<style>
html,
body {
  height: 100%;
  margin: 0;
  padding: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100%;
  width: 100%;
}
</style>
