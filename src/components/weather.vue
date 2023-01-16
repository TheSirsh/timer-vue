<template>
  <div>
    <input type="text" class="city" />
    <i class="weather-icon owf"></i>
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
            icon: String,
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
    mounted() {
      fetch('https://api.openweathermap.org/data/2.5/weather?q=Saint%20Petersburg&lang=en&appid=a930528912396a5ecf6b0001ff49f152&units=metric')
        .then(response => response.json())
        .then(json => {
          this.weatherData = json
        })
    }
  }
</script>
