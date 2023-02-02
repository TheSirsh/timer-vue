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
    }
  },
  mounted() {
    this.langSet(this.lang);
  },
  methods: {
    changeLang() {
      let lang = (this.lang === "EN") ? "RU" : "EN";
        this.lang = lang;
        this.langSet(this.lang);
    },
    langSet(str) {
      if (str === "EN") {
        this.title = EN.settingsTitle;
        this.langButton = EN.settingsLang;
      } else {
        this.title = RU.settingsTitle;
        this.langButton = RU.settingsLang;
      }
    }
  }
}
</script>