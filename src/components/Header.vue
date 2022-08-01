<template>
    <header class="header">
        <a class="home" href="#">
            <img src="../assets/logo.svg" alt="logo">
            <span class="logo">ZebreShop</span>
        </a>
        <ul class="links">
            <li><a href="#">Boutique</a></li>
            <li><a href="#">Admin</a></li>
        </ul>
        <ul>
            <li><a href="#">Connexion</a></li>
            <li><a href="#">Inscription</a></li>
        </ul>
    </header>
</template>

<script lang="ts" setup>

</script>

<style lang="scss" scoped>
    .header {
        display: flex;
        flex-direction: row;
        align-items: center;
    }
    .home {
        display: flex;
        flex-direction: row;
        align-items: center;
        margin-right: 1.25rem;
        img {
            width: 2.8125rem;
            margin-right: .3125rem;;
        }
        .logo {
            font-weight: bold;
            font-size: 1.25rem;
            color: var(--text-primary-color);
        }
    }
    ul {
        display: flex;
        flex-direction: row;
        li {
            margin-right: .625rem;
            a {
                color: var(--text-primary-color);
            }
        }
    }
    .links {
        flex: 1 1 auto;
    }
</style>