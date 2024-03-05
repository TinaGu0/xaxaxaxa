<template>
    <div class="item">
        <p>{{ item.name }}</p>
        <button @click="remove">Remove</button>
    </div>
</template>

<script>
import { store } from '../views/store.js'

export default {
    name: "CartArray",
    props: {
        item: Object,
        cart: Array,
    },
    methods: {
        remove() {
            store.cart.splice(this.index, 1);
        }
    }
}

</script>

<style scoped>
.item {
    background-color: #FFF;
    margin-bottom: 2vw;
}

</style>