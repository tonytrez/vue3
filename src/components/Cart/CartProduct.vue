<template>
    <div class="product">
        <strong>{{ product.title }}</strong>
        <span class="quantity">x{{ product.quantity }}</span>
        <span>{{ product.price }}€</span>
        <button class="btn btn-danger" @click="$emit('remove', product.id)">Supprimer</button>
    </div>
</template>

<script lang="ts" setup>
import type { ProductCartInterface } from '@/interfaces';

    defineProps<{
        product: ProductCartInterface
    }>();

    defineEmits<{
        (e: 'remove', productId: number): void
    }>()
</script>

<style lang="scss" scoped>
    .product {
        background-color: var(--gray-1);
        display: flex;
        flex-direction: row;
        align-items: center;
        strong {
            margin-right: .625rem;
        }
        button {
            margin-right: .625rem;
        }
        span {
            margin-right: .625rem;
        }
    }
    .quantity {
        flex: 1 1 auto;
    }
</style>