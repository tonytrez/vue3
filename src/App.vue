<script lang="ts" setup>
    import Header from './components/Header.vue';
    import Footer from './components/Footer.vue';
    import Cart from './components/Cart/Cart.vue';
    import Shop from './components/Shop/Shop.vue';
    import { reactive } from 'vue';
    import data from './data/products';
    import type { ProductInterface, ProductCartInterface } from './interfaces';
import { computed } from '@vue/reactivity';

    const state = reactive<{
        products: ProductInterface[],
        productsAdded:ProductCartInterface[]
    }>({
        products: data,
        productsAdded: []
    })

    function addProduct(productId: number) {
        const product = state.products.find(product => product.id === productId);
        if (undefined !== product) {
            const productInCart = state.productsAdded.find(productAdded => productAdded.id === product.id);
            if (undefined !== productInCart) {
                productInCart.quantity++;
            } else {
                state.productsAdded.push(product);
            }
        }
    }

    function removeProduct(productId: number) {
        const productInCart = state.productsAdded.find(productAdded => productAdded.id === productId);
        if (undefined !== productInCart) {
            if (productInCart.quantity > 1) {
                productInCart.quantity--;
            } else {
                state.productsAdded = state.productsAdded.filter(product => product.id !== productId);
            }
        }
    }

    const cartEmpty = computed(() => state.productsAdded.length === 0);

</script>

<template>
<div class="app-container" :class="{gridEmpty: cartEmpty}">
    <Header class="header"/>
    <Shop class="shop" @add="addProduct" :products="state.products"/>
    <Cart 
        class="cart"
        v-if="false === cartEmpty" 
        :productsAdded="state.productsAdded" 
        @remove="removeProduct"
    />
    <Footer class="footer"/>
</div>
</template>


<style lang="scss">
    @import './assets/scss/base.scss';
    @import './assets/scss/debug.scss';

    .app-container {
        min-height: 100vh;
        display: grid;
        grid-template-areas: 'header header' 'shop cart' 'footer footer';
        grid-template-columns: 75% 25%;
        grid-template-rows: 3rem auto 3rem;
    }
    .gridEmpty {
        grid-template-areas: 'header' 'shop' 'footer';
        grid-template-columns: 100%;
    }
    .header {
        grid-area: header;
        background-color: var(--primary-1);
    }
    .shop {
        grid-area: shop;
        background-color: var(--gray-1);
    }
    .cart {
        grid-area: cart;
        padding: .625rem;
        border: var(--border);
    }
    .footer {
        grid-area: footer;
    }

</style>