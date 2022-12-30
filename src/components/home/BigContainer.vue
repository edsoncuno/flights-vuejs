<script setup>
import Container from "./Container.vue";
</script>
<template>
    <div class="bigcontainer">
        <Container />
    </div>
</template>

<style scoped>
.bigcontainer {
    width: 100vw;
    height: auto;
    /*
    height: 90vh;
    */
    display: flex;
    justify-content: center;
    align-items: top;
}
</style>