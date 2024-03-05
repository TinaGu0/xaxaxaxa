<template>
  <h1>Board Games</h1>
  
    <div class="display">
      <ProductCard
      v-for = "game in games" 
      :key = "game.name"
      :game = "game"
      />
    </div>
  
    <div class="addToCart">
        <h2>Shopping Cart</h2>
        <h3>Items in Cart: {{ store.count }}</h3>
        <h3>Total Price: {{ store.price }}</h3>
        <CartArray 
        v-for = "item in store.cart"
        :key = "index"
        :item = "item"
        />
      </div>
  </template>
  
  <script setup>
  import {store} from '../views/store.js';
  import ProductCard from '@/components/ProductCard.vue';
  import CartArray from '@/components/CartArray.vue';
  
let props = defineProps({
  index: Object,
})

  const games = [
    {
      name: "Monopoly",
      price: "$20",
      img: "https://m.media-amazon.com/images/I/812z45q0jYL._AC_SX679_.jpg",
    },
    {
      name: "Guess Who?",
      price: "$16",
      img: "https://m.media-amazon.com/images/I/81LN0nlRQML._AC_SX679_.jpg",
    },
    {
      name: "Sorry!",
      price: "$10",
      img: "https://m.media-amazon.com/images/I/91ABJdVWwyL._AC_SX679_.jpg",
    },
    {
      name: "Trouble",
      price: "$13.62",
      img: "https://m.media-amazon.com/images/I/81ofxH9uLrL._AC_SX679_.jpg",
    },
    {
      name: "Battleship",
      price: "$17",
      img: "https://m.media-amazon.com/images/I/71GcJTrP0HL._AC_UF894,1000_QL80_.jpg",
    },
    {
      name: "The Game of Life",
      price: "$20",
      img: "https://dmzn2b8hkpq8b.cloudfront.net/images/products/515x515/S304518_1.jpg",
    },
    {
      name: "Connect Four",
      price: "$12",
      img: "https://m.media-amazon.com/images/I/71FGqk1RfVL._AC_SX679_.jpg",
    },
    {
      name: "Clue",
      price: "$22",
      img: "https://m.media-amazon.com/images/I/81x-QjeZrDL._AC_SX679_.jpg",
    },
    {
      name: "Sequence",
      price: "$15",
      img: "https://m.media-amazon.com/images/I/81FKvz4ijFL._AC_SX679_.jpg",
    },
  ]
  
  </script>
  
  <style scoped>
  h1 {
    font-family: 'Hind', sans-serif;
    background-color: var(--secondary);
    margin: 4rem 35rem 1.5rem;
    border-radius: 1rem;
    font-size:3rem;
  }
  
  .display {
  display: flex;
  flex-wrap: wrap;
  width: 92vw;
  margin: 1rem 2rem;
  align-items: center;
  justify-content: left;
  }
  
  .addToCart {
    height: 95%;
    width: 300px;
    position: fixed;
    top: 0;
    right: 0;
    background-color: var(--secondary);
    padding-top: 20px;
    margin-top: 2rem;
    overflow-y: scroll;
  }
  
  h3 {
    margin: 1rem;
  }
  </style>