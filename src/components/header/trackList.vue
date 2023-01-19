<template>
  <ol class="play-list">
    <li class="playItem"
    v-for="track in trackList" :key="track.title">
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

<style>
  .play-list {
    text-align: left;
  }

  .playItem {
    position: relative;
    padding: calc(100vw / 204.8);
    padding-left: calc(100vw / 51.2);
    list-style: none;
    opacity: .8;
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
</style>