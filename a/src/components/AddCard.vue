<template>
    <div>
        <button class="btn" @click="increment(), total()">Add to Cart</button>
    </div>
</template>

<script>
import { store } from '../views/store.js'

export default {
  name: "AddCard",
  props: {
    game: Object,
    cart: Array,
  },
  components: {
  }, 
  methods: {
    increment() {
        store.count++
    },
    total() {
        store.cart.push(this.game)
        console.log(store.cart)
}
  }
}

</script>

<style scoped>
.btn {
background-color: var(--tertiary);
padding: 0.5rem;
font-size: 1.1rem;
margin: 1rem auto;
border: solid var(--primary);
}
</style>