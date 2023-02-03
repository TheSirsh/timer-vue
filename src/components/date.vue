<template>
  <p class="date">
    {{ months[curMonth] }}, {{ daysName[curDay] }} {{ curDateNum }}
  </p>
</template>

<script>
import { default as EN } from "@/assets/json/langEN";
import { default as RU } from "@/assets/json/langRU";

export default {
  name: "Date",
  data() {
    return {
      months: [],
      daysName: [],
      curMonth: Number,
      curDay: Number,
      curDateNum: Number,
      lang: String,
      langData: Object,
    }
  },
    mounted() {
      this.lang = localStorage.getItem("lang");
      this.langData = (this.lang === "EN") ? (EN) : (RU);
      this.setText(this.langData);
      this.setDate()
      setInterval(() => this.setDate(), 500);
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
    },
    setText(obj) {
      this.months = obj.months;
      this.daysName = obj.months;
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