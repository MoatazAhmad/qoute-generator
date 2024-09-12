<script setup>
import { inject, onMounted , ref} from "vue";

import QuoteCard from "./quoteCard.vue";

const qoutesData = inject("quotes");

const qouteText = ref();
const qoutesAuthor = ref();

function randomQoute() {
  if (qoutesData && qoutesData.length > 0) {
    const randomElement = qoutesData[Math.floor(Math.random() * qoutesData.length)];
    qouteText.value = randomElement.text; // Assign quote text
    qoutesAuthor.value = randomElement.author; // Assign quote author
  } else {
    console.error("No quotes available!");
  }
}
onMounted(()=>{
  randomQoute()
}) 
// next step is to select teh button of new qoute , on click the genquote function is execute
function handleClick() {
  randomQoute()
}
function handleTweet() {
  const tweetURL = `https://twitter.com/intent/tweet?text=${encodeURIComponent(qouteText.value)} - ${encodeURIComponent(qoutesAuthor.value)}`;
  window.open(tweetURL, "tweet window", "width=600,height=300");
}
</script>
<template lang="pug">
    .quote-box 
      q {{qouteText}}
      span {{qoutesAuthor}}
    div.buttons
      button(class="gen-quote" @click="handleClick") New Quote  
      button(class="tweet" @click="handleTweet") 
        img(src="../assets/images/twitter.png")  
        | Tweet 
</template>
<style lang="scss">
.quote-box {
  q {
    display: block;
    width: 100%;
    font-size: 26px;
    min-height: 110px;
  }
  span {
    position: relative;
    float: right;
    &::after {
      content: "";
      display: inline-block;
      background: rgb(23, 124, 229);
      left: -40%;
      position: absolute;
      top: 50%;
      width: 30%;
      height: 2px;
    }
  }
}
.buttons {
  width: 100%;
  margin-top: 50px;
  display: flex;
  justify-content: center;
  button {
    border: none;
    border-radius: 30px;
    margin-right: 10px;
    border: 1px solid rgb(23, 124, 229);
    width: 150px;
    height: 50px;
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 5px;
    cursor: pointer;
  }
  .gen-quote {
    background: rgb(23, 124, 229);
    color: white;
  }
  .tweet {
    background: white;
    color: black;
    img {
      width: 20px;
      height: 20px;
      object-fit: contain;
      margin-right: 10px;
    }
  }
}
</style>
