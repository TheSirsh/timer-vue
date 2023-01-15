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
          curHour: new Date().getHours(),
          curMin: new Date().getMinutes(),
          curSec: new Date().getSeconds(),
      }
    },
    mounted() {
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
    margin-bottom: calc(100vw / 102.4);
    font-family: 'Arial-MT';
    font-size: calc(100vw / 10.24);
    letter-spacing: -4px; 
  }
</style>