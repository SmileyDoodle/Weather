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
  display: grid;
  min-height: 93vh;
  grid-template-rows: auto 1fr auto;
  background-color: #f5efe7;
}

@media only screen and (min-width: 1024px) {
.home {
  min-height: 100vh;
}
}
</style>