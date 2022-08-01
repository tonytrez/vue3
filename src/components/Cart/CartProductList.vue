<template>
    <div v-for="product in productsAdded">
        <CartProduct class="product" :product="product" @remove="$emit('remove', $event)"/>
    </div>
</template>

<script lang="ts" setup>
import type { ProductCartInterface } from '@/interfaces';
import CartProduct from './CartProduct.vue';
    defineProps<{
        productsAdded: ProductCartInterface[]
    }>();

    defineEmits<{
        (e: 'remove', productId: number): void
    }>()
</script>

<style lang="scss" scoped>
    .product {
        padding: .625rem;
        margin-bottom: .625rem;
        border: var(--border);
        border-radius: var(--border-radius);
    }
</style>