<script setup>
import QuoteCard from "./components/quoteCard.vue";
import QuotesData from "./assets/success.json";
import { provide } from "vue";

provide("quotes", QuotesData)
</script>

<template lang="pug">
  QuoteCard
</template>

<style scoped lang="sass"></style>

