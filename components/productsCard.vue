<template>
    <div class="card group relative width-400-pixels height-500-pixels">
        <img :src="product.images[0]" :alt="product.description">
        <h3>{{ product.title }}</h3>
        <p>{{ product.description }}</p>
        <div class="flex flex-row justify-between items-center">
            <p>Prix: {{ product.price }} €</p>
            <button class="add-to-cart-button" @click="addToCart">Ajouter au panier </button>
        </div>
    </div>
  </template>
  
<script>
  export default {
    props: {
      product: {
        type: Object,
        required: true,
      },
    },
    methods: {
        addToCart() {
            this.$emit('add-to-cart', this.product);
        }
    }
  };
</script>
  
<style scoped>
.card {
    width: 300px;
    margin: 10px;
    padding: 10px;
    border: 1px solid #ccc;
}

img {
    max-width: 100%;
    max-height: 100%;
}
.add-to-cart-button {
    background-color: lightskyblue;
    color: #ffffff;
}
</style>
