<script setup>
import LogoBox from './LogoBox.vue';
import LinkBox from "./LinkBox.vue"
</script>

<template>
    <header class="header">
        <LogoBox />
        <LinkBox />
    </header>
</template>

<style scoped>
.header {
    width: 100vw;
    height: 100px;
    background-color: white;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
}
</style>