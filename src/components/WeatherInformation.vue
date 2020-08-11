<template>
  <div class="right-wrap">
        <div class="weather-wrap" v-if="weather">
        <h1 id="title"> {{ weather.name }} </h1>
        <div class=centering-wrap>
            <div class="temperature">
                <div class="temperature-wrap">
                <h1>{{ (weather.main.temp).toFixed(0) }}° </h1>
                </div>
                <div class="min-max-wrap">
                <p>
                    ↑ {{ (weather.main.temp_max).toFixed(0) }}°
                </p>
                <p>
                    ↓ {{ (weather.main.temp_min).toFixed(0) }}°
                </p>
                </div>
                <div>
                    <button @click="$emit('unit-metric')" :class="{ selected: selectedUnit === unitC }" >°C</button>
                    <button @click="$emit('unit-imperial')" :class="{ selected: selectedUnit === unitF }">°F</button>
                    <!-- <button @click="fetchWeather(unitC)" :class="{ selected: selectedUnit === unitC }" >°C</button>
                    <button @click="fetchWeather(unitF)" :class="{ selected: selectedUnit === unitF }">°F</button> -->
                </div>
            </div>
            <div class="information-wrap">
                <div class="extra-data">
                <p> Feels like: {{ (weather.main.feels_like).toFixed(0) }}° </p>
                <p> Humidity:  {{ weather.main.humidity }}% </p>
                </div>
                <div class="extra-data">
                <p> Pressure: {{ weather.main.pressure }}hPa </p>
                <p> Wind:  {{ weather.wind.speed }}{{ selectedUnit === unitC ? "m/s" : "mph" }}</p>
                </div>
            </div>
        </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'WeatherInformation',
    props: ['weather', 'unitC', 'unitF', 'selectedUnit']
}
</script>

<style>
.right-wrap {
  display: flex;
  width: 50%;
}
.weather-wrap {
  display: flex;
  flex-direction: column;
  text-align: center;
  align-items: center;
  margin: 0 auto;
  min-width: 450px;
}
#title {
  font-family: 'Nunito', sans-serif;
  font-weight: 400;
  font-size: 3rem;
  text-align: center;
  padding-top: 2rem;
  vertical-align: top;
}
.centering-wrap {
  width: 80%;
}
.temperature {
  display: flex;
  justify-content: center;
  padding-top: 3rem;
}
.information-wrap {
  display: flex;
  justify-content: center;
  padding-top: 1rem;
}
.temperature-wrap h1 {
  font-family: 'Nunito', sans-serif;
  font-weight: 300;
  font-size: 6rem;
}
.min-max-wrap p {
  font-size: 1.5rem;
  padding-top: 1.3rem;
  padding-left: 1rem;
  padding-right: 1.2rem;
}
.extra-data {
  text-align: left;
  padding-right: 1.2rem;
}
button {
  background-color: transparent;
  border: none;
  padding-top: 1.6rem;
  font-size: 1rem;
  cursor: pointer;
}
.selected {
  color: #fdaf1f;
  font-weight: 700;
}
button:focus {
  outline: none;
}
</style>