<template>
  <div class="container">
    <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
    <!--   <app-new-quote @quoteAdded="newQuote"></app-new-quote> -->
    <app-new-quote></app-new-quote>
    <app-quote-grid :quotes="quotes"></app-quote-grid>
    <div class="row">
      <div class="col-sm-12 text-center">
        <div
          class="alert alert-info"
          v-if="quotes.length>0"
        >Info: Haz click en una cita para borrarla</div>
      </div>
    </div>
  </div>
</template>

<script>
import { eventBus } from "./main";
import QuoteGrid from "./components/QuoteGrid.vue";
import NewQuote from "./components/NewQuote.vue";
import Header from "./components/Header.vue";
export default {
  data() {
    return {
      quotes: [],
      maxQuotes: 10
    };
  },
  methods: {
    newQuote(quote) {
      if (this.quotes.length >= this.maxQuotes) {
        alert("Por favor, elimina una cita antes");
        return;
      }
      this.quotes.push(quote);
    }
  },
  components: {
    appQuoteGrid: QuoteGrid,
    appNewQuote: NewQuote,
    appHeader: Header
  },
  created() {
    eventBus.$on("quoteAdded", quote => {
      if (this.quotes.length >= this.maxQuotes) {
        alert("Por favor, elimina una cita antes");
        return;
      }
      this.quotes.push(quote);
    });
    eventBus.$on("deleteQuote", index => {
      this.quotes.splice(index, 1);
    });
  }
};
</script>

<style>
</style>
