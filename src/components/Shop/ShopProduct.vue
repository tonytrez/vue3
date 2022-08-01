<template>
    <div class="product">
        <div class="product-image" :style="{backgroundImage: `url(${product.image})`}"></div>
        <div class="product-description">
            <h2>{{ product.title }}</h2>
            <p>{{ product.description }}</p>
            <div class="control">
                <strong>Prix: {{ product.price }}€</strong>
                <button class="btn btn-primary" @click="emit('add', product.id)">Ajouter au panier</button>
            </div>
        </div>
    </div>
</template>

<script lang="ts" setup>
import type { ProductInterface } from '@/interfaces/Product.interface';

defineProps<{
    product: ProductInterface
}>();

const emit = defineEmits<{
    (e:'add', productId: number): void
}>();

</script>

<style lang="scss" scoped>
 .product {
    padding: .625rem;
    display: flex;
    flex-direction: column;
    margin-top: 1.25rem;
    border: var(--border);
    border-radius: var(--border-radius);
    background-color: white;
    &-image {
        border-top-left-radius: var(--border-radius);
        border-top-right-radius: var(--border-radius);
        background-size: cover;
        background-repeat: no-repeat;
        background-position: center;
        height: 12.5rem;
    }
    &-description {
        display: flex;
        flex-direction: column;
        h2 {
            margin-bottom: .3125rem;
            margin-top: .3125rem;
        }
    }
 }
.control {
    margin-top: .3125rem;
    display: flex;
    flex-direction: row;
    align-items: center;
    strong {
        flex: 1 1 auto;
    }
}
</style>