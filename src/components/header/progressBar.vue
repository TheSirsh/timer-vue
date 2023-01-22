<template>
  <div class="trackTitle">
    <span class="trackName">{{playList[playNum].title}}</span>
  </div>
  <div class="audioProgressBarBg"
    ref="audioBlock"
    v-on:click="changeAudio($event)"
  >
    <div class="audioProgressBar"
      :style="{width: setAudioProgress(curTime)}"
    ></div>
  </div>
  <div class="trackControl">
    <span class="trackProgress">
      {{convertTime(curTime)}} / {{convertTime(playList[playNum].duration)}}
    </span>
    <div class="muteButton on"
      v-if="isSound"
      v-on:click="toogleSound"
    ></div>
    <div class="muteButton off"
      v-else
      v-on:click="toogleSound"
    ></div>
    <div class="volumeProgressBarBg"
        ref="volBlock"
        v-on:click="changeVolume($event)"
    ><div class="volumeProgressBar"
        :style="{ width: setVolume(vol) }"
      ></div>
    </div>
  </div>
</template>

<script>
import { default as playList } from "@/assets/json/playListData.js";

export default {
  name: "Audio Control",
  emits: ["newVol", "newCurTime", ],
  props: {
    playNum: Number,
    curTime: Number,
  },
  data() {
    return {
      trackTitle: String,
      vol: 0.3,
      isSound: true,
      playList,
      translateX: Number,
      audioWidth: Number,
      volWidth: Number,
    }
  },
  components: {
    playList,
  },
  mounted() {
    this.playList = playList;
    this.updateVolumeWidth();
    this.updateAudioWidth();
  },
  methods: {
    convertTime: function(dur) {
      const min = Math.floor(dur / 60);
      const sec = dur - min * 60;
      return (sec < 10) ? (min + ":0" + sec) : (dur =  min + ":" + sec);
    },
    setAudioProgress: function(time) {
      return time / playList[this.playNum].duration * 100 + "%";
    },
    toogleSound: function() {
      this.isSound = !this.isSound;
      this.vol = (this.isSound === false) ? 0 : 0.3;
    },
    changeAudio: function(event) {
      this.updateAudioWidth();
      this.translateX = event.offsetX;
      const curTime = this.translateX / this.audioWidth * playList[this.playNum].duration
      this.$emit("newCurTime", {curTime: curTime})
    },
    changeVolume: function(event) {
      this.updateVolumeWidth();
      this.translateX = event.offsetX;
      this.vol = this.translateX / this.volWidth;
      this.isSound = true;
      this.setVolume();
    },
    setVolume: function() {
      this.$emit("newVol",{ vol: this.vol });
      return this.vol * 100 + "%";
    },
    updateAudioWidth: function() {
      const audioWidth = this.$refs.audioBlock.clientWidth;
      this.audioWidth = audioWidth;
    },
    updateVolumeWidth: function() {
      const volWidth = this.$refs.volBlock.clientWidth;
      this.volWidth = volWidth;
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
    max-width: 100%;
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