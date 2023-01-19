<template>
  <header class="header">
    <player/>
    <weather/>
  </header>
</template>

<script>
  import weather from "@/components/weather.vue"
  import player from "@/components/header/audioPlayer.vue"
  
  export default {
    name: "UpperSection",
    components: {
      player, weather
    }
  }

</script>

<style>

.header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  width: 100%;
  height: 30vh;
  max-height: 220px;  
  padding: 1vw;
}

</style>
