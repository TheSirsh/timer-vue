<template>
  <div class="quote-block">
    <button class="change-quote"
      v-on:click="changeQuote"
    ></button>
    <div>
      <div class="quote">
        {{quote}}
      </div>
      <div class="author">
        {{author}}
      </div>
    </div>
  </div>  
</template>

<script>
import {default as quoteList} from "@/assets/json/quotes.js"

export default {
  name: "Quotes",
  data() {
    return {
      quoteList: [],
      num: Number,
      quote: String,
      author: String,
    }
  },
  components: {
    quoteList
  },
  mounted() {
    this.quoteList = quoteList
    this.changeQuote()
  },
  methods: {
    changeQuote: function() {
      this.num = Math.floor(Math.random() * (this.quoteList.length));
      this.quote = quoteList[this.num].quoteText;
      this.author = quoteList[this.num].quoteAuthor;
    },
  }
}
</script>

<style scope>
  .quote-block {
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    align-items: center;
    width: 60%;
    height: 30vh;
    padding: 0.5vw;
    margin: 0px auto;
  }

  .change-quote {
    width: calc(100vw / 32);
    height: calc(100vw / 32);
    background-size: calc(100vw / 32) calc(100vw / 32);
    background-position: center center;
    background-repeat: no-repeat;
    background-color: transparent;
    border: 0;
    outline: 0;
    opacity: .8;
    cursor: pointer;
    transition: .3s;   margin-bottom: calc(100vw / 34.13);
    background-image: url("../assets/svg/reload.svg");  
  }

  .quote {
    min-height: calc(100vw / 32);
  }

  .author {
    min-height: calc(100vw / 51.2);
  }
</style>