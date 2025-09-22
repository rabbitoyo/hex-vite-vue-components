<script setup>
import { inject } from 'vue'

// 產品列表父傳子
defineProps({
    products: {
        type: Array,
        required: true,
    },
})

// 加入購物車子傳父
const emit = defineEmits(['add-cart'])
const showNotification = inject('showNotification')
const handleAddCart = (product) => {
    emit('add-cart', product)
    showNotification(`商品 ${product.name} 已加入購物車`, 'success')
}
</script>

<template>
    <div class="col-md-8">
        <h2 class="mb-3">商品列表</h2>
        <div class="row">
            <div class="col-md-4 mb-4" v-for="product in products" :key="product.id">
                <div class="card h-100">
                    <img :src="product.image" class="card-img-top" :alt="product.name" />
                    <div class="card-body">
                        <h5 class="card-title">{{ product.name }}</h5>
                        <p class="card-text">{{ product.description }}</p>
                        <p class="fw-bold text-primary">${{ product.price }}</p>
                        <button class="btn btn-success w-100" @click="handleAddCart(product)">
                            加入購物車
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped></style>
