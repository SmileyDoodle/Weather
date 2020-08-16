<template>
  <div class="right-wrap">
        <div class="weather-wrap" v-if="weather">
        <h1 id="title"> {{ weather.name }} </h1>
        <div class=centering-wrap>
            <div class="temperature">
                <div class="temperature-left-wrap">
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
                </div>
                <div>
                    <button @click="$emit('unit-metric')" :class="{ selected: selectedUnit === unitC }" >°C</button>
                    <button @click="$emit('unit-imperial')" :class="{ selected: selectedUnit === unitF }">°F</button>
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
}
.weather-wrap {
  display: flex;
  flex-direction: column;
  text-align: center;
  align-items: center;
  margin: 0 auto;
  width: 100%;
}
#title {
  font-family: 'Nunito', sans-serif;
  font-weight: 400;
  font-size: 1.8rem;
  text-align: center;
  padding-top: 0.5rem;
  vertical-align: top;
}
.centering-wrap {
  width: 60%;
}
.temperature {
  display: flex;
  justify-content: space-between;
  padding-top: 1rem;
}
.temperature-left-wrap{
  display: flex;
}
.information-wrap {
  display: flex;
  justify-content: space-between;
  padding-top: 1rem;
}
.temperature-wrap h1 {
  font-family: 'Nunito', sans-serif;
  font-weight: 300;
  font-size: 4rem;
}
.min-max-wrap p {
  font-size: 0.7rem;
  padding-top: 1.3rem;
  padding-left: 0.5rem;
  text-align: left;
}
.extra-data {
  text-align: left;
}
.extra-data p {
  font-size: 0.7rem;
}
button {
  background-color: transparent;
  border: none;
  padding-top: 1.2rem;
  font-size: 0.7rem;
  cursor: pointer;
  opacity: 0.3;
  transition: opacity ease 0.5s;
}
button:hover {
  opacity: 1;
  transition: opacity ease 0.5s;
}
.selected {
  color: #527690;
  font-weight: 700;
  opacity: 1;
}
button:focus {
  outline: none;
}

@media only screen and (min-width: 1024px) {
.right-wrap  {
  width: 50%;
}
#title {
  font-size: 3rem;
  padding-top: 3.5rem;
}
.centering-wrap {
  width: 70%;
}
.temperature {
  padding-top: 3.3rem;
}
.temperature-wrap h1 {
  font-size: 6rem;
}
.min-max-wrap p {
  font-size: 1.5rem;
  padding-left: 1rem;
  padding-right: 1.2rem;
}
.extra-data p {
  font-size: 1.1rem;
  padding-top: 0.2rem;
}
button {
  padding-top: 1.6rem;
  font-size: 1rem;
}
}
</style>