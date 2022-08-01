<template>
    <footer class="footer">
        <p>Copyright © 2014-{{ year }} TonyTrez</p>
    </footer>
</template>

<script lang="ts" setup>
    const date = new Date();
    const year = date.getFullYear();
</script>

<style lang="scss" scoped>
    .footer {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: center;
        background-color: var(--primary-2);
    }
</style>