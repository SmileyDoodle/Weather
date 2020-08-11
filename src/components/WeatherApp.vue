<template>
      <main>
        <div class="main-wrap">
          <!-- search bar -->
          <div class="search-box">
              <div class="control is-medium" :class="{'is-loading': isLoading}">
                  <input class="input is-rounded is-medium" type="text" placeholder="City..." v-model="query" @keyup.enter="fetchWeather(unitC)"/>
              </div>
          </div>
          <!-- fetched information -->
          <div class="content-wrap">
            <!-- left-side -->
            <WeatherIcons 
              :weather="weather" 
              v-if="weather"
            ></WeatherIcons>
            <!-- right-side -->
            <WeatherInformation 
              :weather="weather"
              :unitC="unitC"
              :unitF="unitF"
              :selectedUnit="selectedUnit"
              v-if="weather"
              @unit-metric="fetchWeather(unitC)"
              @unit-imperial="fetchWeather(unitF)"
            ></WeatherInformation>
            <div v-if="error">{{error}}</div>
          </div> 
        </div>
      </main>  
</template>

<script>
import WeatherIcons from '@/components/WeatherIcons.vue'
import WeatherInformation from '@/components/WeatherInformation.vue'

export default {
  name: 'WeatherApp',
  components: {
    WeatherIcons,
    WeatherInformation
  },
  data () {
    return {
    api_key: process.env.VUE_APP_API_KEY,
    url_base: process.env.VUE_APP_URL_BASE,
    query: "",
    cityName: "",
    weather: "",
    isLoading: false,
    unitC: `units=metric`,
    unitF: `units=imperial`,
    selectedUnit: "",
    error: ""
    }
  },
  methods: {
    fetchWeather (unit) {
        this.error = '';
        this.isLoading = true;
        this.selectedUnit = unit;
        if (this.query !== "") {
          this.cityName = this.query;
        }
        fetch(`${this.url_base}weather?q=${this.cityName}&appid=${this.api_key}&${unit}`)
          .then(res => {
            return res.json();
          }).then(result => {
            console.log('result ', result);
            
            if(result.cod === 200) {
              this.weather = result;
            } else {
              this.error = result.message;
            }
            this.isLoading = false;
            this.query = "";
          }).catch((err) => {
            // console.log(err);
            this.isLoading = false;
            this.query = "";
            this.error = err;
          })
    },
}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
main {
  padding: 0 5rem;
  width: 1380px;
  margin: 0 auto;
}
.main-wrap {
  background-color: #f6f3ec;
  border-radius: 30px;
  box-shadow: 3px 5px 10px 2px #444;
  display: grid;
  padding: 3rem;
  height: 75vh;
}
.search-box {
  min-width: 400px;
  max-width: 650px;
  margin: 0 auto;
}
.content-wrap {
  display: flex;
}
</style>
