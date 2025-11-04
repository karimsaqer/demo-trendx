<template>
  <div id="app">
    <Header />
    <Hero />
    <HeroVideo />
    <TravelOffers />
    <Activities />
    <About />
    <Contact />
    <Footer />
  </div>
</template>

<script>
import Header from "./components/TheHeader.vue";
import Hero from "./components/TheHero.vue";
import TravelOffers from "./components/TravelOffers.vue";
import About from "./components/About.vue";
import Contact from "./components/Contact.vue";
import Footer from "./components/Footer.vue";
import HeroVideo from "./components/HeroVideo.vue";
import Activities from "./components/Activities.vue";

export default {
  name: "App",
  components: {
    Header,
    Hero,
    TravelOffers,
    About,
    Contact,
    Footer,
    HeroVideo,
    Activities,
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

#app {
  width: 100%;
}

:root {
  --primary-color: #3489b6;
  --secondary-color: #feaf0c;
  --text-dark: #333;
  --text-light: #666;
  --white: #ffffff;
  --gray-bg: linear-gradient(to right, #e3f2fd, #f5faff);
  --black: #1f1f1f;
  --light: #b0b0b0;
}
</style>
