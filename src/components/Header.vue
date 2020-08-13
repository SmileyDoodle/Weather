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
  padding: 3rem 5rem 0;
  justify-content: center;
}
.logo-icon {
  /* color: #f6f3ec; */
  height: 38px;
}
.logo {
  /* color: #fff; */
  font-family: 'Nunito', sans-serif;
  font-weight: 400;
  font-size: 1.5rem;
  text-align: center;
}
</style>