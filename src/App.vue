<template>
  <div id="app">
    <weather/>
    <clock/>
    <date/>
    <greetings/>
  </div>
</template>

<script>
import weather from "@/components/weather.vue"
import clock from "@/components/clock.vue"
import date from "@/components/date.vue"
import greetings from "@/components/greetings.vue"

export default {
  name: '#app',
  components: {
    weather, clock, date, greetings
  }
}
</script>

<style>
  #app {
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }

  body {
    min-width: 480px;
    min-height: 100vh;
    max-width: 100vw;
    max-height: 100vh;
    font-family: 'Arial', sans-serif;
    font-size: calc(100vw / 64);
    color: #fff;
    text-align: center;
    background: url("./assets/img/bg.jpg") center/cover, rgba(0, 0, 0, 0.5);
    background-blend-mode: multiply;
    transition: background-image 1s ease-in-out;
    overflow: hidden;
  }
</style>
