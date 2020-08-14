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
  padding: 2rem 5rem 1.5rem;
  justify-content: center;
}
.logo-icon {
  height: 25px;
}
.logo {
  font-family: 'Nunito', sans-serif;
  font-weight: 400;
  text-align: center;
}

@media only screen and (min-width: 1024px) {
.header {
  padding: 3rem 5rem 0;
}
.logo-icon {
  height: 38px;
}
.logo {
  font-size: 1.5rem;
}
}
</style>