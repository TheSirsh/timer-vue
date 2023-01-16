<template>
  <div class="weather">
    <input type="text" class="city" />
    <i class="weather-icon owf"
      v-bind:class="iconClass"
    ></i>
    <div class="weather-error"></div>
    <div class="description-container">
      <span class="temperature"> {{ weatherData.main.temp }} °C</span>
      <span class="weather-description"> {{ weatherData.weather[0].description }} </span>
    </div>
    <div class="wind">Wind speed: {{ weatherData.wind.speed }} m/s</div>
    <div class="humidity">Humidity: {{ weatherData.main.humidity }}%</div>
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
        }
      }
    },
    computed: {
      iconClass: function() {
        return "owf-" + this.weatherData.weather[0].id
        
      }
    },
    mounted() {
      fetch('https://api.openweathermap.org/data/2.5/weather?q=Saint%20Petersburg&lang=en&appid=a930528912396a5ecf6b0001ff49f152&units=metric')
        .then(response => response.json())
        .then(json => {
          this.weatherData = json
        })
    }
  }
</script>

<style scoped>
  @import url("../assets/css/owfont-regular.css");

  .weather {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: flex-start;
    row-gap: calc(100vw / 204.8);
    width: calc(100vw / 5.69);
    min-height: 180px;  
    text-align: left;
    font-size: calc(100vw / 85);
  }

  .weather-error {
    margin-top: calc(100vw / (-102.4));
  }

  .description-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: flex-start;
    align-items: center;
    column-gap: calc(100vw / 85.3);
  }

  .weather-icon {
    font-size: calc(100vw / 23.27);
  }
</style>>
