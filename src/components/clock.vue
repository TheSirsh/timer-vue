<template>
  <time class="clock">
    {{ curHour }} : {{ curMin }} : {{ curSec }}
  </time>
</template>

<script>
  export default {
    name: "Clock",
    data() {
      return {
          curHour: Number,
          curMin: Number,
          curSec: Number,
      }
    },
    mounted() {
      this.setTime();
      setInterval(() => this.setTime(), 500);
    },
    methods: {
      setTime() {
        const curDate = new Date();
          let curSec = curDate.getSeconds();
            curSec = (curSec < 10) ? ("0" + curSec.toLocaleString()) : curSec.toLocaleString();
            this.curSec = curSec;
          let curMin = curDate.getMinutes();
            curMin = (curMin < 10) ? ("0" + curMin.toLocaleString()) : curMin.toLocaleString();
            this.curMin = curMin;
          let curHour = curDate.getHours();
            curHour = (curHour < 10) ? ("0" + curHour.toLocaleString()) : curHour.toLocaleString()
            this.curHour = curHour;
      }
    }
  }
</script>

<style scoped>
  .clock {
    min-height: calc(100vw / 8.26);
    margin-bottom: 0.5vw;
    font-family: 'Arial-MT';
    font-size: calc(100vw / 10.24);
    letter-spacing: -4px; 
  }
</style>