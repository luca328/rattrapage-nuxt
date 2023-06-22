<template>
    <div>
        <div class="flex justify-center items-center" v-if="loadingState">
            <Icon class="" size="80" name="svg-spinners:bars-scale"/>
        </div>
        <div class="card-container">
            <ProductCard v-for="product in products" :key="product.title" :product="product" @add-to-cart="addToCart"/>
        </div>
    </div>
</template>

<script setup>
import ProductCard from '@/components/productsCard.vue';

const cart = [];
const products = ref([]);
const loadingState = ref(true)

function addToCart(product) {
  cart.push(product);
}

async function getProducts() {
    const productsApi = await fetch('https://dummyjson.com/products')
    const productsJson = await productsApi.json()
    products.value = productsJson.products
    loadingState.value = false
}

onMounted(() => {
    loadingState.value = true
    getProducts()
})
</script>