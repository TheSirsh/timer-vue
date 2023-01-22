<template>
  <ol class="play-list">
    <li class="playItem"
    v-for="track in playList" :key="track.title"
    v-bind:class="{active: track.index === playNum}">
      {{track.title}} {{trackLength(track.duration)}}
    </li>
  </ol>
  
</template>

<script>
import playListData from "@/assets/json/playListData.js";

export default {
  name: "trackList",
  props: {
    playNum: Number,
  },
  data() {
    return {
      playList: playListData,
      dur: "",
    }
  },
  components: {
    playListData,
  },
  methods: {
    trackLength: function(dur) {
      const min = Math.floor(dur / 60);
      const sec = dur - min * 60;
      return (sec < 10) ? (min + ":0" + sec) : (dur =  min + ":" + sec);
    },
  }
}
</script>

<style>
  .play-list {
    text-align: left;
    padding-left: 2vw;
  }

  .playItem {
    position: relative;
    padding: calc(100vw / 204.8);
    list-style: none;
    opacity: .5;
    cursor: pointer;
    transition: .3s;
    z-index: 1;
  }

  .playItem:hover {
    opacity: 1;
  }

  .playItem::before {
    position: absolute;
    left: 0;
    top: 2px;
    font-weight: 900;
  }

  .active {
    opacity: 1;
  }
</style>