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

            switch (iconID) {
              case "01d":
                this.image = "01.svg";
                break;
              case "01n":
                this.image = "01.2.svg";
                break;
              case "02d":
                this.image = "02.svg";
                break;
              case "02n":
                this.image = "02.2.svg";
                break;
              case "03d":
              case "03n":
                this.image = "03.svg";
                break;
              case "04d":
              case "04n":
                this.image = "04.svg";
                break;
              case "09d":
              case "09n":
              case "10d":
              case "10n":
                this.image = "05.svg";
                break;
              case "11d":
              case "11n":
                this.image = "06.svg";
                break;
              case "13d":
              case "13n":
                this.image = "07.svg";
                break;
              case "50d":
              case "50n":
                this.image = "08.svg";
                break;
              default:
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
}
.img-wrap {
  width: 100%;
  display: flex;
  flex-direction: column;
}
.img-box {
  height: 200px;
} 
#weatherMain {
  font-family: 'Nunito', sans-serif;
  font-weight: 400;
  font-size: 1.8rem;
  text-align: center;
  padding-top: 2rem;
}

@media only screen and (min-width: 1024px) {
.left-wrap  {
  width: 45%;
}
.img-box {
  height: 350px;
}
#weatherMain {
  font-size: 3rem;
  padding-top: 3.5rem;
}
}
</style>