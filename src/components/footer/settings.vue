<template>
  <div class="settings">
    <h2 class="settings__title">
      {{ title }}
    </h2>
    <div class="settings__lang">
      {{ langButton }}
    </div>
  </div>
</template>

<script>
import { default as EN } from "@/assets/json/langEN";

export default {
  name: "Settings",
  data() {
    return {
      title: "",
      langButton: "",
    }
  },
  mounted() {
    this.title = EN.settingsTitle;
    this.langButton = EN.settingsLang
  },
}
</script>