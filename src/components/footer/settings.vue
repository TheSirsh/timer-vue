<template>
  <div class="settings">
    <h2 class="settings__title">
      {{ title }}
    </h2>
    <div class="settings__lang"
      v-on:click="changeLang"
    >
      {{ langButton }}
    </div>
  </div>
</template>

<script>
import { default as EN } from "@/assets/json/langEN";
import { default as RU } from "@/assets/json/langRU";

export default {
  name: "Settings",
   data() {
    return {
      title: "",
      langButton: "",
      lang: "EN",
      langData: Object,
    }
  },
  mounted() {
    this.lang = localStorage.getItem("lang");
    this.langData = (this.lang === "EN") ? (EN) : (RU);
    this.setText(this.langData);
  },
  methods: {
    changeLang() {
      this.lang = (this.lang === "EN") ? ("RU") : ("EN");
      this.langData = (this.lang === "EN") ? (EN) : (RU);
      localStorage.setItem("lang", this.lang);
      this.setText(this.langData);
    },
    setText(obj) {
      this.title = obj.settingsTitle;
      this.langButton = obj.settingsLang;
    }
  }
}
</script>