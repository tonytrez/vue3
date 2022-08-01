<template>
    <div>
        <h1 class="title">Panier</h1>
        <CartProductList class="list" :productsAdded="productsAdded" @remove="$emit('remove', $event)"/>
        <button class="btn btn-success">Commander ({{ totalPrice }}€)</button>
    </div>
</template>

<script lang="ts" setup>
import type { ProductCartInterface } from '@/interfaces';
import { computed } from '@vue/reactivity';
import CartProductList from './CartProductList.vue';
    const props = defineProps<{
        productsAdded: ProductCartInterface[]
    }>();

    defineEmits<{
        (e: 'remove', productId: number): void
    }>()

    const totalPrice = computed(() => 
        props.productsAdded.reduce((acc, product) => acc + product.price * product.quantity, 0));
</script>

<style lang="scss" scoped>
    .list {
        display: flex;
        flex-direction: column;
    }
    .title {
        margin-bottom: .625rem;
    }
</style>