<template>
  <p class="date">
    {{ months[curMonth] }}, {{ daysName[curDay] }} {{ curDateNum }}
  </p>
</template>

<script>
import { default as EN } from "@/assets/json/langEN";

export default {
  name: "Date",
  data() {
    return {
      months: [],
      daysName: [],
      curMonth: Number,
      curDay: Number,
      curDateNum: Number,
    }
  },
    mounted() {
      this.setDate()
      setInterval(() => this.setDate(), 500);
      this.months = EN.months;
      this.daysName = EN.months;
    },
  methods: {
    setDate() {
        const curDate = new Date();
          let curMonth = curDate.getMonth();
            this.curMonth = curMonth;
          let curDay = curDate.getDay();
            this.curDay = curDay;
          let curDateNum = curDate.getDate();
            this.curDateNum  = curDateNum
    }
  }
}
</script>

<style>
  .date {
    min-height: calc(100vw / 36.57);
    font-size: calc(100vw / 42.67);
    margin: 0.5vw auto;
  }
</style>