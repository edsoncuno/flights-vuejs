<script setup>
import LinkButton from "./LinkButton.vue";
</script>

<template>
    <nav class="linkbox">
        <LinkButton route="/home" text="Flights" />
        <LinkButton route="/admin" text="Admin" />
    </nav>
</template>

<style scoped>
.linkbox {
    height: 80px;
    margin: 18px 10px;
    align-self: flex-end;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
}
</style>