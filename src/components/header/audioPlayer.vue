<template>
  <div class="player">
    <div class="player-controls">
      <button class="play-prev player-icon"
        v-on:click="prevTrack"
      ></button>
      <button class="play player-icon"
        v-on:click="playTrack"
      ></button>
      <button class="play-next player-icon"
        v-on:click="nextTrack"
      ></button>
    </div>
      <trackList/>
  </div>
</template>

<script>
import trackList from "@/components/header/trackList.vue";
import { default as playListData } from "@/assets/json/playListData.js";

export default {
  name: "audioplayer",
  data() {
    return {
      playListData: [],
      playNum: 0,
      track: new Audio(),
    }
  },
  components: {
    trackList, playListData,
  },
  computed: {
    playTrack: function() {
      this.track.src = playListData[this.playNum].src;
      this.track.play();
    },
  },
  methods: {
    nextTrack: function() {
      this.playNum = (this.playNum === playListData.length - 1) ? (this.playNum = 0) : (this.playNum = this.playNum + 1);
      this.playTrack;
    },
    prevTrack: function() {
      this.playNum = (this.playNum === 0) ? (this.playNum = playListData.length - 1) : (this.playNum = this.playNum - 1);
      this.playTrack;
    }
  }
}
</script>

<style>
  .player-controls {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: calc(100vw / 8.53);
    margin-bottom: calc(100vw / 60);
  }

  .player-icon {
    width: calc(100vw / 32);
    height: calc(100vw / 32);
    background-size: calc(100vw / 32) calc(100vw / 32);
    background-position: center center;
    background-repeat: no-repeat;
    background-color: transparent;
    border: 0;
    outline: 0;
    opacity: .8;
    cursor: pointer;
    transition: .3s;  
  }

  .player-icon:hover {
    opacity: 1;
  }

  .player-icon:active {
    border: 0;
    outline: 0;  
    transform: scale(1.1);
  }

  .play {
    width: calc(100vw / 25.6);
    height: calc(100vw / 25.6);
    background-size: calc(100vw / 25.6) calc(100vw / 25.6);
    background-image: url("../../assets/svg/play.svg");
  }

  .pause {
    background-image: url("../../assets/svg/pause.svg");
  }

  .play-prev {
    background-image: url("../../assets/svg/play-prev.svg");
  }

  .play-next {
    background-image: url("../../assets/svg/play-next.svg");
  }
</style>