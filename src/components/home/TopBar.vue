<script setup>
defineProps({
    isLoadingList: {
        type: Boolean
    }
})
</script>

<template>
    <div class="topbar">
        <div class="titulo">
            Find Flights
            <div class="loading" v-if="isLoadingList">LOADING FLIGHTS, PLEASE WAIT ! </div>
        </div>
    </div>
</template>

<style scoped lang="scss">
.topbar {
    background-color: white;
    width: 100%;
    height: 40px;
    display: flex;
    justify-content: flex-start;
    align-items: center;

    .titulo {
        margin-left: 20px;

        .loading {
            font-size: 0.8em;
            color: red;
        }
    }
}
</style>