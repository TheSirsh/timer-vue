<template>
    <div class="greeting-container">
      <span class="greeting">
        {{ greetings }}{{ dayParts[curDayPart] }},
      </span>
      <input type="text" class="name"
        v-bind:placeholder="placeholder"
      />
    </div>
</template>

<script>
import { default as EN } from "@/assets/json/langEN";

export default {
  name : "Greetings",
  data() {
    return {
      greetings: "",
      dayParts: [],
      curDayPart: Number,
      placeholder: "",
    }
  },
  mounted() {
    this.dayParts = EN.dayParts;
    this.greetings = EN.greetings;
    this.placeholder = EN.greetingsPlaceholder;
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
    width: 100vw;
    font-size: calc(100vw / 25.6);
  }

  .greeting {
    flex: 1;  
    padding: 0.5vw;
    text-align: right;
  }

  .name {
    flex: 1;
    width: auto;
    max-width: 50%;
    padding: 0.5vw;
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
