<template>
    <div v-for="product in products">
        <ShopProduct @add="emit('add', $event)" :product="product"/>
    </div>
</template>

<script lang="ts" setup>
    import type { ProductInterface } from '@/interfaces/Product.interface';
    import ShopProduct from './ShopProduct.vue';
    defineProps<{
        products: ProductInterface[]
    }>()
    const emit = defineEmits<{
        (e: 'add', productId: number): void
    }>();
</script>

<style lang="scss" scoped></style>