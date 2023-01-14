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
    background-color: black;
    font-family: "alarm clock";
    font-size: 3vw;
    border-radius: 1vw;
    padding: 1vw;
    color: #fff;
    text-shadow:
        0 0 7px #fff,
        0 0 10px #fff,
        0 0 21px #fff,
        0 0 42px #0fa,
        0 0 82px #0fa,
        0 0 92px #0fa,
        0 0 102px #0fa,
        0 0 151px #0fa;
  }
</style>