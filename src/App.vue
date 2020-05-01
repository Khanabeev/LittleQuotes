<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        <h2>Little Quote</h2>
        <v-icon class="ml-2">fas fa-quote-right</v-icon>
      </div>

      <v-spacer></v-spacer>
    </v-app-bar>

    <v-content>
      <quote-progress-bar
              :quotes-qnt="quotes.length"
              :max-quotes="maxQuotes"
              :is-maximum="isMaximum"
      ></quote-progress-bar>
      <new-quote
              @addQuote="newQuote"
              :is-maximum="isMaximum"
      ></new-quote>
      <quote-grid
              :quotes="quotes"
              @deleteOneQuote="deleteQuote"
      ></quote-grid>
    </v-content>
  </v-app>
</template>

<script>

import QuoteGrid from "@/components/QuoteGrid";
import NewQuote from "@/components/NewQuote";
import QuoteProgressBar from "@/components/QuoteProgressBar";
export default {
  name: 'App',
  components: {QuoteProgressBar, NewQuote, QuoteGrid},

  data: () => ({
    maxQuotes: 10,
    quotes: []
  }),

  computed: {
    isMaximum: function () {
      return this.quotes.length >= this.maxQuotes;
    }
  },
  watch: {
    isMaximum: function (val) {
      if (val) {
        alert('You have reached the limit of quotes! Deletes some of them.')
      }
    }
  },
  mounted() {
    if (localStorage.getItem("quotes") === null) {
      localStorage.setItem('quotes','')
    } else {
      let savedQuotes = localStorage.getItem("quotes");
      this.quotes = JSON.parse(savedQuotes);
    }
  },
  methods: {
    newQuote: function (quote) {
      let randStr = Math.random().toString(36).substring(2, 5) + Math.random().toString(36).substring(2, 5);
      this.quotes.push({id: randStr, text: quote});
      localStorage.setItem('quotes',JSON.stringify(this.quotes));
    },
    deleteQuote: function (index) {
      this.quotes.splice(index,1);
      localStorage.setItem('quotes', JSON.stringify(this.quotes));
    }
  }
};
</script>
