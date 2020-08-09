<template>
  <div class="home">
    <Header></Header>
    <WeatherApp></WeatherApp>
    <Footer></Footer>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import WeatherApp from '@/components/WeatherApp.vue'
import Footer from '@/components/Footer.vue'
import Header from '@/components/Header.vue'

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
  /* background-color: #f6f3ec; */
  background-color: #214458;
  background-image: url("https://www.transparenttextures.com/patterns/low-contrast-linen.png");
}
</style>