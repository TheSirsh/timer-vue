<template>
    <div class="greeting-container">
      <span class="greeting">
        Good {{ dayParts[curDayPart] }},
      </span>
      <input type="text" class="name" placeholder="Enter your name"/>
    </div>
</template>

<script>
export default {
  name : "Greetings",
  data() {
    return {
      dayParts: ["Night", "Morning", "Afternoon", "Evening"],
      curDayPart: Number
    }
  },
  mounted() {
    setInterval(() => this.setGreetings(), 1000)
  },
  methods: {
    setGreetings() {
      const curHour = new Date().getHours();
        let curDayPart = Math.floor(curHour / 8) + 1
        this.curDayPart = curDayPart
    }
  }
}
</script>
