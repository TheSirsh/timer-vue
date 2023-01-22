<template>
  <div class="player">
    <div class="player-controls">
      <button class="play-prev player-icon"
        v-on:click="prevTrack"
      ></button>
      <button class="play player-icon"
        v-on:click="playTrack"
        v-if="!isPlay"
      ></button>
      <button class="pause player-icon"
        v-on:click="pause"
        v-else
      ></button>
      <button class="play-next player-icon"
        v-on:click="nextTrack"
      ></button>
    </div>
      <audioControl
        :playNum="playNum"
        :curTime="curTime"
        @newVol="updVol"
        @newCurTime="newTime"
      />
      <trackList/>
  </div>
</template>

<script>
import trackList from "@/components/header/trackList.vue";
import { default as playListData } from "@/assets/json/playListData.js";
import audioControl from "@/components/header/progressBar.vue"

export default {
  name: "audioplayer",
  data() {
    return {
      playListData: [],
      playNum: 0,
      track: new Audio(),
      isPlay: false,
      curTime: 0,
      vol: Number,
    }
  },
  components: {
    trackList, playListData, audioControl,
  },
  mounted() {
      setInterval(() => this.updTime(this.track), 500);
  },
  methods: {
    playTrack: function() {
      this.track.src = playListData[this.playNum].src;
      this.track.play();
      this.isPlay = true;
    },
    pause: function() {
      this.track.pause();
      this.isPlay = false;
    },
    nextTrack: function() {
      this.playNum = (this.playNum === playListData.length - 1) ? (this.playNum = 0) : (this.playNum = this.playNum + 1);
      this.track.currentTime = 0;
      this.playTrack();
      this.isPlay = true;
    },
    prevTrack: function() {
      this.playNum = (this.playNum === 0) ? (this.playNum = playListData.length - 1) : (this.playNum = this.playNum - 1);
      this.track.currentTime = 0;
      this.playTrack();
      this.isPlay = true;
    },
    updTime: function(track) {
      let curTime = track.currentTime;
      this.curTime = Math.floor(curTime);
      if (curTime >= track.duration) { this.nextTrack() }
    },
    updVol: function(vol) {
      this.track.volume = vol.vol;
    },
    newTime: function(time) {
      this.track.currentTime = time.curTime;
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

  .play,
  .pause {
    width: calc(100vw / 25.6);
    height: calc(100vw / 25.6);
    background-size: calc(100vw / 25.6) calc(100vw / 25.6);
  }

  .play {
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