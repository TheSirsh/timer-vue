<template>
  <footer class="footer">
    <settings/>
    <quotes/>
    <toDo/>
  </footer>
</template>

<script>
import quotes from "@/components/footer/quotes.vue";
import toDo from "@/components/footer/toDoList.vue";
import settings from "@/components/footer/settings.vue";

export default {
  components: {
    settings, quotes, toDo,
  }
}
</script>

<style>
  .footer {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
    height: 30vh;
    min-height: calc(100vw / 6.4);
  }
</style>