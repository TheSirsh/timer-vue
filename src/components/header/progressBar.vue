<template>
  <div class="trackTitle">
    <span class="trackName">{{playList[playNum].title}}</span>
  </div>
  <div class="audioProgressBarBg">
    <div class="audioProgressBar"></div>
  </div>
  <div class="trackControl">
    <span class="trackProgress"></span>
    <div class="muteButton on"></div>
    <div class="volumeProgressBarBg"></div>
    <div class="volumeProgressBar"></div>
  </div>
</template>

<script>
import { default as playList } from "@/assets/json/playListData.js";

export default {
  name: "Audio Control",
  props: {
    playNum: Number
  },
  data() {
    return {
      trackTitle: String,
      playList
    }
  },
  components: {
    playList
  },
  mounted() {
    this.playList = playList
  },
}
</script>

<style>
  .audioProgressBarBg {
    width: calc(100vw / 6);
    margin-bottom: 5px;
    height: 10px;
    background-color: #FFFFFF;
    cursor: pointer;
  }

  .audioProgressBar {
    width: 0%;
    height: 10px;
    background-color: #C5B358;
  }
</style>