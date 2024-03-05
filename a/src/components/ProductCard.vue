<template>
  <div class="gamecard">
      <h2>{{ game.name }}</h2>
      <h2>{{ game.price }}</h2>
  <img :src = "game.img" alt="" />
  <AddCard :game = "game"/>
  </div>

</template>

<script>
import AddCard from './AddCard.vue'

export default {
  name: "ProductCard",
  props: {
    game: Object,
    cart: Array,
    index: Object,
  },
  components: {
    AddCard,
  }, 
}



</script>

<style scoped>
img {
width: 50%;
height: 10rem;
margin-top: 1.5rem;
}
.gamecard {
width: 25%;
background-color: var(--secondary);
display: flex;
flex-direction: column;
align-items: center;
justify-content: space-around;
border-radius: 1rem;
margin: 25px 25px;
box-shadow: 1rem 1rem 0.5rem var(--tertiary);
padding-bottom: 40px;
}

</style>