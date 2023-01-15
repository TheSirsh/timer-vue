<template>
  <div id="app">
    <clock/>
    <date/>
  </div>
</template>

<script>
import clock from "@/components/clock.vue"
import date from "@/components/date.vue"
export default {
  name: '#app',
  components: {
    clock, date
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
