<script setup>
import PaneSearch from "./PaneSearch.vue";
import PaneFlights from "./PaneFlights.vue";

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
    <div class="pane">
        <PaneSearch :search="search" />
        <PaneFlights :list="list" />
    </div>
</template>

<style>
.pane {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}
</style>