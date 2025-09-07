<script setup>
import { computed, inject } from 'vue'

// 購物車父傳子
const { carts } = defineProps({
    carts: {
        type: Array,
        required: true,
    },
})

// 移除購物車子傳父
const emit = defineEmits(['remove-cart'])
const showNotification = inject('showNotification')
const handleRemoveCart = (item) => {
    emit('remove-cart', item)
    showNotification(`已移除 ${item.name} `, 'error')
}

// 計算購物車是否為空
const isCartEmpty = computed(() => carts.length === 0)

// 計算單項商品總價（用 function 包起來）
const itemTotal = (item) => item.price * item.quantity

// 計算總金額
const totalAmount = computed(() => {
    return carts.reduce((sum, item) => sum + item.price * item.quantity, 0)
})
</script>

<template>
    <div class="col-md-4">
        <h2 class="mb-3">購物車</h2>
        <div v-if="isCartEmpty">購物車是空的</div>
        <ul class="list-group mb-3">
            <li
                class="list-group-item d-flex justify-content-between align-items-center"
                v-for="item in carts"
                :key="item.id"
            >
                <div>
                    <h6 class="my-0">{{ item.name }}</h6>
                    <small class="text-muted">數量：{{ item.quantity }}</small>
                </div>
                <div>
                    <span class="text-muted">${{ itemTotal(item) }}</span>
                    <button
                        class="btn btn-sm btn-outline-danger ms-2"
                        @click="handleRemoveCart(item)"
                    >
                        移除
                    </button>
                </div>
            </li>
        </ul>
        <!-- ✅ 總金額區 -->
        <div class="d-flex justify-content-between fw-bold">
            <span>總金額</span>
            <span>${{ totalAmount }}</span>
        </div>
    </div>
</template>

<style scoped></style>
