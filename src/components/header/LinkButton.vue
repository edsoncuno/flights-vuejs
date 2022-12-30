<script setup>
import { RouterLink } from 'vue-router';

defineProps({
    route: {
        type: String,
        required: true
    },
    text: {
        type: String,
        required: true
    }
})
</script>

<template>
    <RouterLink :to=route>
        <button class="button">{{ text }}</button>
    </RouterLink>
</template>

<style scoped>
button {
    border-radius: 9px;
    width: 100px;
    height: 30px;
    background-color: #415D65;
    color: white;
    text-align: center;
}
</style>