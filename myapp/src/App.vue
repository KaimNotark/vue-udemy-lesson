<template>
  <div id="app">
    <!-- <img alt='Vue logo' src='./assets/logo.png' />

    <HelloWorld msg='Welcome to Your Vue.js App' /> -->
    <h1>{{ firstName }}</h1>
    <h1>{{ num + 2 }}</h1>
    <h3>{{ num > 2 ? "Number: > 2" : "Number: < 2" }}</h3>
    <a :[attrKey]="linkUrl">Go to Google</a>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "App",
  components: {
    HelloWorld
  },
  data: () => ({
    firstName: "Denis",
    num: 2,
    linkUrl: "https://google.com",
    attrKey: "href"
  })
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
