<template>
  <ol>
    <li v-for="track in trackList" :key="track.title">
      {{track.title}}
    </li>
  </ol>
  
</template>

<script>
import playList from "@/assets/json/playList.json"

export default {
  name: "trackList",
  data() {
    return {
      trackList: playList
    }
  },
}
</script>