<script setup>
import { inject } from 'vue'

const notifications = inject('notifications')
</script>

<template>
    <div class="position-fixed top-0 end-0 p-3" style="z-index: 1050">
        <div
            class="toast show align-items-center text-white bg-success border-0 mb-2"
            :class="{
                'bg-success': n.type === 'success',
                'bg-danger': n.type === 'error',
                'bg-info': n.type === 'info',
            }"
            v-for="n in notifications"
            :key="n.id"
        >
            <div class="d-flex">
                <div class="toast-body">{{ n.message }}</div>
                <button
                    type="button"
                    class="btn-close btn-close-white me-2 m-auto"
                    @click="notifications.splice(notifications.indexOf(n), 1)"
                ></button>
            </div>
        </div>
    </div>
</template>

<style scoped></style>
