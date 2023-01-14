<template>
  <div id="app">
    <clock/>
  </div>
</template>

<script>
import clock from "@/components/clock.vue"
export default {
  name: '#app',
  components: {
    clock
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
