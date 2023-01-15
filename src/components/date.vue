<template>
  <p>
    {{ months[curMonth] }}, {{ daysName[curDay] }} {{ curDateNum }}
  </p>
</template>

<script>
export default {
  name: "Date",
  data() {
    return {
      day: new Date().getDate(),
      months: ["January", "February", "March", "April", "May", "June", "July", "August", "September", "November", "December"],
      daysName: [ "Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"],
      curMonth: new Date().getMonth(),
      curDay: new Date().getDay(),
      curDateNum: new Date().getDate(),
    }
  },
    mounted() {
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
    }
  }
}
</script>
