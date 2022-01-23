<template>
  <div class="m-0">
    <Navbar />
    <Header />
    <Shortener />
    <CallToAction />
    <Footer />
  </div>
</template>

<script>
import "./assets/tailwind.css";
import Navbar from "./components/Navbar.vue";
import Header from "./components/Header.vue";
import Shortener from "./components/Shortener.vue";
import CallToAction from "./components/CallToAction.vue";
import Footer from "./components/Footer.vue";

export default {
  name: "App",
  components: {
    Navbar,
    Header,
    Shortener,
    CallToAction,
    Footer,
  },
};
</script>

<style>
</style>
