<template>
      <main>
        <div class="main-wrap">
          <div class="search-box">
              <div class="control is-medium" :class="{'is-loading': isLoading}">
                  <input class="input is-rounded is-medium" type="text" placeholder="City..." v-model="query" @keyup.enter="fetchWeather(unitC)"/>
              </div>
          </div>

          <div class="content-wrap">
            <div class="left-wrap">
              <div class="img-wrap" v-if="weather">
                  <h1 id="weatherMain"> {{weather.weather[0].main}} </h1>
                  <img class="img-box" :src="require(`../assets/images/${image}`)" alt="icon">
              </div>
            </div>

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
                            <button @click="fetchWeather(unitC)" :class="{ selected: selectedUnit === unitC }" >°C</button>
                            <button @click="fetchWeather(unitF)" :class="{ selected: selectedUnit === unitF }">°F</button>
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

              <div v-if="error">{{error}}</div>
          </div>

         
        </div>
      </main>  
</template>

<script>
export default {
  name: 'WeatherApp',
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
    iconID: "",
    currentIconID: "",
    image: "",
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
            // console.log(`import:`, res.json());
            
            return res.json();
          }).then(result => {
            console.log('result ', result);
            
            if(result.cod === 200) {
              this.weather = result;
              this.changeIcon(); 

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
    
    changeIcon () {
        const iconID = this.weather.weather[0].icon;
        if (this.iconID !== "") {
          this.currentIconID = this.iconID;
        }

        if (iconID === "01d" || iconID === "01n") {
          this.image = "01.svg";
        } else if (iconID === "02d" || iconID === "02n") {
          this.image = "02.svg";
        } else if (iconID === "03d" || iconID === "03n") {
          this.image = "03.svg";
        } else if (iconID === "04d" || iconID === "04n") {
          this.image = "04.svg";
        } else if (iconID === "09d" || iconID === "09n" || iconID === "10d" || iconID === "10n") {
          this.image = "05.svg";
        } else if (iconID === "11d" || iconID === "11n") {
          this.image = "06.svg";
        } else if (iconID === "13d" || iconID === "13n") {
          this.image = "07.svg";
        } else if (iconID === "50d" || iconID === "50n") {
          this.image = "08.svg";
        } else {
          this.image = "03.svg";
        }
    },

}}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

main {
  padding: 0 5rem;
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
.img-wrap {
  width: 100%;
  display: flex;
  flex-direction: column;
}
.content-wrap {
  display: flex;
}
.left-wrap {
  display: flex;
  width: 45%;
}
#weatherMain {
  font-family: 'Nunito', sans-serif;
  font-weight: 400;
  font-size: 3rem;
  text-align: center;
  padding-top: 2rem;
}
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




img {
  height: 350px;
} 

</style>
