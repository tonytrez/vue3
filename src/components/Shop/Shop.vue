<template>
    <div class="list">
        <ShopProductList @add="emit('add', $event)" :products="products" />
    </div>  
</template>

<script lang="ts" setup>
import ShopProductList from './ShopProductList.vue';
import type { ProductInterface } from '@/interfaces/Product.interface';

    defineProps<{
        products: ProductInterface[]
    }>();
    const emit = defineEmits<{
        (e: 'add', productId: number): void
    }>();
</script>

<style lang="scss" scoped>
    .list {
        display: flex;
        flex-direction: row;
        justify-content: space-evenly;
        flex-wrap: wrap;
    }
</style>