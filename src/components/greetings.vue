<template>
    <div class="greeting-container">
      <span class="greeting">
        Good {{ dayParts[curDayPart] }},
      </span>
      <input type="text" class="name" placeholder="Enter your name"
      />
    </div>
</template>

<script>
export default {
  name : "Greetings",
  data() {
    return {
      dayParts: ["Night", "Morning", "Afternoon", "Evening"],
      curDayPart: Number,
    }
  },
  mounted() {
    this.setGreetings();
    setInterval(() => this.setGreetings(), 1000);
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

<style>
  .greeting-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  min-height: calc(100vw / 21.33);
  width: 100vw;
  font-size: calc(100vw / 25.6);
  }

  .greeting {
    flex: 1;  
    padding: calc(100vw / 102.4);
    text-align: right;
  }

  .name {
    flex: 1;
    width: auto;
    max-width: 50%;
    padding: calc(100vw / 102.4);
    font-size: calc(100vw / 25.6);
    text-align: left;
    color: #fff;
    background-color: transparent;
    border: 0;
    outline: 0;
  }

  .name::placeholder {
    color: #fff;
    opacity: .6;
  }
</style>
