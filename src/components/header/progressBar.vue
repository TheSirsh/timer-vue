<template>
  <div class="trackTitle">
    <span class="trackName">{{playList[playNum].title}}</span>
  </div>
  <div class="audioProgressBarBg">
    <div class="audioProgressBar"
      :style="{width: setAudioProgress(curTime)}"
    ></div>
  </div>
  <div class="trackControl">
    <span class="trackProgress">
      {{convertTime(curTime)}} / {{convertTime(playList[playNum].duration)}}
    </span>
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
    playNum: Number,
    curTime: Number,
  },
  data() {
    return {
      trackTitle: String,
      playList,
    }
  },
  components: {
    playList
  },
  mounted() {
    this.playList = playList
  },
  methods: {
    convertTime: function(dur) {
      const min = Math.floor(dur / 60);
      const sec = dur - min * 60;
      return (sec < 10) ? (min + ":0" + sec) : (dur =  min + ":" + sec);
    },
    setAudioProgress: function(time) {
      return time / playList[this.playNum].duration * 100 + "%"
    }
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

  .trackControl {
    width: calc(100vw / 6);
    display: flex;
    font-size: calc(100vw / 85.3);
    justify-content: space-between;
    align-items: center;
  }

  .muteButton {
    width: calc(100vw / 70);
    height: calc(100vw / 70);
    background-size: calc(100vw / 70) calc(100vw / 70);
    cursor: pointer;
  }

  .on {
    background-image: url("../../assets/svg/volume.svg");
  }

  .off {
    background-image: url("../../assets/svg/mute.svg");
  }

  .volumeProgressBarBg {
    width: calc(100vw / 15);
    margin-bottom: 5px;
    height: 5px;
    background-color: #FFFFFF;
    cursor: pointer;
  }

  .volumeProgressBar {
    width: 0%;
    height: 5px;
    background-color: #C5B358;
  }
</style>