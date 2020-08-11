<template>
      <div class="left-wrap">
        <div class="img-wrap" v-if="weather && image">
            <h1 id="weatherMain"> {{weather.weather[0].main}} </h1>
            <img class="img-box" :src="require(`../assets/images/${image}`)" alt="icon">
        </div>
      </div>
</template>

<script>
export default {
    name: 'WeatherIcons',
    props: ['weather'],
    data() {
        return {
            iconID: "",
            currentIconID: "",
            image: "",
        }
    },
    methods: {
        changeIcon () {
            const iconID = this.weather.weather[0].icon;
            if (this.iconID !== "") {
            this.currentIconID = this.iconID;
            }
            // console.log(iconID);
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
    },
    mounted() {
        this.changeIcon();
    },
    updated: function () {
        this.$nextTick(function () {
            this.changeIcon();
            // Code that will run only after the
            // entire view has been re-rendered
        })
    }
}
</script>

<style>
.left-wrap {
  display: flex;
  width: 45%;
}
.img-wrap {
  width: 100%;
  display: flex;
  flex-direction: column;
}
.img-box {
  height: 350px;
} 
#weatherMain {
  font-family: 'Nunito', sans-serif;
  font-weight: 400;
  font-size: 3rem;
  text-align: center;
  padding-top: 2rem;
}
</style>