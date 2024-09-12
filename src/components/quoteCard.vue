<script setup>
import Quote from "./quote.vue";
// code plan
// 1-write the HTML of the page
// 2- style the page
// 3- make JS logic of the page and fetch the data from the API
</script>
<template lang="pug">
div(class="card d-flex align-items-center")
  h1 Quote of the day
  Quote
</template>
<style lang="scss">
.card {
  padding: 40px;
  text-align: center;
  display: flex;
  align-items: center;
  width: 700px;
  border-radius: 10px;
  box-shadow: 0px 10px 20px 0px rgba(0, 0, 0, 0.15);
  h1 {
    position: relative;
    font-size: 32px;
    margin-bottom: 40px;
    font-weight: bold;
    &::after {
      content: "";
      position: absolute;
      width: 30%;
      height: 2px;
      background: rgb(23, 124, 229);
      left: 50%;
      bottom: -12px;
      transform: translateX(-50%);
    }
  }
}
@media (max-width:705px) {
  .card {
    height: 80vh;
    width: 625px;
    justify-content: center;
    h1 {
      margin-bottom: 100px;
    }
  }
}
@media (max-width:576px) {
  .card {
    width: 325px;
    h1 {
      // margin-bottom: 100px;
    }
  }
}
</style>
