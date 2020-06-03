<template>
  <div id="app">
    <Header />
    <AddQuote />
    <QuoteList />
  </div>
</template>

<script>
import Header from './components/Header';
import AddQuote from './components/Add-quote';
import QuoteList from './components/Quote-list';

  export default {
    name: 'App',

    methods: {
    },

    components: {
      Header,
      AddQuote,
      QuoteList
    }
  }
</script>

<style>

body {
  text-align: center;
  font-size: 16px;
  color: #000;
}

</style>
