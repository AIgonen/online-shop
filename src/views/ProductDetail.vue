<template>
    <div class="product">
        <div class="product-image">
            <img :src="selectedProduct.thumbnail" alt="">
            <div class="product-details">
                <p>Brand: {{ selectedProduct.brand }}</p>
                <p>Description: {{ selectedProduct.description }}</p>
                <p>Price> ${{ selectedProduct.price }}</p>
            </div>
        </div>
    </div>
</template>

<script>
    import { defineComponent } from 'vue';
    //import route from 'vue-route';

    export default defineComponent({
        name: 'ProductDetails',

    })
</script>

<script setup>
import {  computed } from 'vue'
import {productStore} from '@/stores/products'
import { useRoute } from 'vue-router'


const store = productStore()
const route = useRoute()

const selectedProduct = computed( () => {
        return store.products.find((item) => item.id === Number(route.params.id))
    }) 
</script>

<style scoped>
.product {
  display: flex;
  margin-top: 50px;
}

.product-image {
  margin-right: 24px;
}

</style>