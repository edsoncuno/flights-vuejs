<script setup>
import Pane from "./Pane.vue";

defineProps({
    list: {
        type: Array
    },
    search: {
        type: Function
    }
})
</script>

<template>
    <div class="background">
        <Pane :list="list" :search="search" />
    </div>
</template>

<style>
.background {
    background: linear-gradient(rgba(255, 255, 255, .5), rgba(255, 255, 255, .5));
    width: 100%;
    height: auto;
    min-height: 400px;
}
</style>