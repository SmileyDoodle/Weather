<template>
  <div class="home">
    <Header></Header>
    <WeatherApp></WeatherApp>
    <Footer></Footer>
  </div>
</template>

<script>
// @ is an alias to /src
import Header from '@/components/Header.vue'
import WeatherApp from '@/components/WeatherApp.vue'
import Footer from '@/components/Footer.vue'

export default {
  name: 'Home',
  components: {
    Header,
    WeatherApp,
    Footer
  }
}
</script>

<style>
.home {
  display: flex;
  flex-direction: column;
  height: 100vh;
  overflow: hidden;
  width: 100%;
  background-color: #f5efe7;
  /* background-color: #214458; */
  /* background-image: url("https://www.transparenttextures.com/patterns/low-contrast-linen.png"); */
}
</style>