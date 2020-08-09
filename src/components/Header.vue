<template>
  <header>
      <img class="logo-icon" src="../assets/images/02.svg" alt="sun">
      <h1 class="logo">
          WeatherApp
      </h1>
  </header>
</template>

<script>
export default {
    name: 'Header'
}
</script>

<style>
header {
  display: flex !important;
  padding: 3rem 5rem 2rem;
  justify-content: center;
}
.logo-icon {
  /* color: #f6f3ec; */
  height: 50px;
}
.logo {
  color: #f6f3ec;
  font-family: 'Nunito', sans-serif;
  font-weight: 400;
  font-size: 2rem;
  text-align: center;
}
</style>