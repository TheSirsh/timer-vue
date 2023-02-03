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
import { default as RU } from "@/assets/json/langRU";

export default {
  name : "Greetings",
  data() {
    return {
      greetings: "",
      dayParts: [],
      curDayPart: Number,
      placeholder: "",
      lang: String,
      langData: Object,
    }
  },
  mounted() {
    this.lang = localStorage.getItem("lang");
    this.langData = (this.lang === "EN") ? (EN) : (RU);
    this.setText(this.langData);
    this.setGreetings();
    setInterval(() => this.setGreetings(), 1000);
  },
  methods: {
    setGreetings() {
      const curHour = new Date().getHours();
        let curDayPart = Math.floor(curHour / 8) + 1
        this.curDayPart = curDayPart
    },
    setText(obj) {
      this.dayParts = obj.dayParts;
      this.greetings = obj.greetings;
      this.placeholder = obj.greetingsPlaceholder;
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
