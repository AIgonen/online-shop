<template>
    <div class="products-list">
        <div class="product" v-for="product in store.products" :key="product.id" @click="goToProductPage(product.id)">
            <img :src="product.thumbnail" alt="">
            <h2>Brand: {{ product.brand }}</h2>
            <p>Description: {{ product.description }}</p>
            <p>Price: ${{ product.price }}</p>
        </div>
    </div>
</template>

<script>
    import { defineComponent } from 'vue';

    export default defineComponent({
        name: 'CatalogView',

    })
</script>


<script setup>
    import { onMounted } from 'vue';
    import { productStore } from '@/stores/products';
    import {useRouter } from 'vue-router'


    const store = productStore()
    const router = useRouter()

    const goToProductPage = (id) => {
        router.push({name: 'ProductView', params: { id }})
    }



    onMounted(() => {
        store.fetchProductsFromDB()
    })
</script>