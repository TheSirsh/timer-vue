<template>
  <footer class="footer">
    <div></div>
    <quotes/>
    <toDo/>
  </footer>
</template>

<script>
import quotes from "@/components/footer/quotes.vue";
import toDo from "@/components/footer/toDoList.vue"

export default {
  data() {
    return {

    }
  },
  components: {
    quotes, toDo,
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