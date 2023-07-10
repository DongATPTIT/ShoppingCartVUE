<template>
  <HeaderApp />
  <BodyApp />
  <FooterApp />
</template>

<script>
import BodyApp from "./components/BodyApp.vue";
import FooterApp from "./components/Footer.vue";
import HeaderApp from "./components/Header.vue";
export default {
  name: "App",
  components: {
    HeaderApp,
    BodyApp,
    FooterApp,
  },
};
</script>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
#app {
  max-width: 1114px;
  margin-left: auto;
  margin-right: auto;
}
</style>