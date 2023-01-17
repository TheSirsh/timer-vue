<template>
  <div class="weather-block">
    <input type="text" class="city" placeholder="Saint Petersburg"
      v-model="city"
      v-on:change="changeCity"
    />
    <div class="weather-error" v-if="err">City is not defined!</div>
    <div class="weather" v-else>
        <i class="weather-icon owf" v-bind:class="iconClass"></i>
        <div class="description-container">
          <span class="temperature"> {{ weatherData.main.temp }} °C</span>
          <span class="weather-description"> {{ weatherData.weather[0].description }} </span>
        </div>
        <div class="wind">Wind speed: {{ weatherData.wind.speed }} m/s</div>
        <div class="humidity">Humidity: {{ weatherData.main.humidity }}%</div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "Weather",
    data() {
      return {
        weatherData: {
          weather: [{
            main: String,
            description: String,
            id: String,
          }],
          main: {
            temp: Number,
            humidity: Number,
          },
          wind: {
            speed: Number
          }
        },
        city: "",
        err: false,
      }
    },
    computed: {
      changeCity: function() {
        let url = "https://api.openweathermap.org/data/2.5/weather?q=" + this.city + "&lang=en&appid=a930528912396a5ecf6b0001ff49f152&units=metric"
        fetch(url)
          .then(response => {
            if (response.ok){
              response.json().then(json => { this.weatherData = json })
              this.err = false
            } else {
              this.err = true
            }
          })
      },
      iconClass: function() {
        return "owf-" + this.weatherData.weather[0].id
      },
    },
    mounted() {
      fetch('https://api.openweathermap.org/data/2.5/weather?q=Saint%20Petersburg&lang=en&appid=a930528912396a5ecf6b0001ff49f152&units=metric')
        .then(response => response.json())
        .then(json => { this.weatherData = json })
    },
  }
</script>

<style scoped>
  @import url("../assets/css/owfont-regular.css");

  .weather-block {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    row-gap: calc(100vw / 204.8);
    width: calc(100vw / 5.69);
    min-height: 180px;  
    text-align: left;
    font-size: calc(100vw / 85);
  }

  .weather {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: flex-start;
    row-gap: calc(100vw / 204.8);
    width: calc(100vw / 5.69);
    min-height: 100px;  
    text-align: left;
    font-size: calc(100vw / 85);
  }

  .weather-error {
    margin-top: 0;
  }

  .city {
    width: calc(100vw / 6.02);
    height: calc(100vw / 30.11);
    padding: calc(100vw / 204.8);
    font-size: calc(100vw / 51.2);
    line-height: calc(100vw / 42.67);
    color: #fff;  
    border: 0;
    outline: 0;
    border-bottom: 1px solid #fff;
    background-color: transparent;
  }

  .city::placeholder {  
    font-size: calc(100vw / 51.2);
    color: #fff;
    opacity: .6;
  }

  .weather-icon {
    font-size: calc(100vw / 23.27);
  }

  .description-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: flex-start;
    align-items: center;
    column-gap: calc(100vw / 85.3);
  }

</style>
