<template>
  <div id="app">
    <Home></Home>
  </div>
</template>

<script>
import Home from './views/Home.vue'

export default {
  name: 'App',
  components: {
    Home
  }
}
</script>

<style>
@import '../node_modules/bulma/css/bulma.css';

html {
  overflow-y: hidden;
}
body {
  font-family: 'Nunito', sans-serif;
  margin: 0;
}
</style>


