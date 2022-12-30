<script setup>
import Create from "../components/admin/Create.vue"
import Pane from "../components/admin/Pane.vue";

import { onMounted, ref } from "vue";

const list = ref([]);
const isLoadingList = ref(true);

const getFlights = async () => {
    const res = await fetch('http://localhost:3000/flights');
    const data = await res.json();
    return data;
}

onMounted(() => {
    getFlights().then((data) => {
        list.value = data
        isLoadingList.value = false;
    });
});

const refresh = () => {
    isLoadingList.value = true;
    getFlights().then((data) => {
        list.value = data
        isLoadingList.value = false;
    });
}
</script>

<template>
    <Create :refresh="refresh" />
    <Pane :list="list" :isLoadingList="isLoadingList" :refresh="refresh" />
</template>