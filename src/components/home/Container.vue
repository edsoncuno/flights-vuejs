<script setup>
import TopBar from "./TopBar.vue";
import Background from "./Background.vue";
import { onMounted, ref } from "vue";

const list = ref([]);
const isLoadingList = ref(true);

const getFlights = async () => {
    const res = await fetch('http://localhost:3000/flights');
    const data = await res.json();
    return data;
}

const getQuery = async (origin, destination) => {
    const res = await fetch(`http://localhost:3000/flights/query/${origin}/${destination}`);
    const data = await res.json();
    return data;
}

onMounted(() => {
    getFlights().then((data) => {
        list.value = data
        isLoadingList.value = false;
    });
});

const search = (origin, destination) => {
    if (origin == "" || destination == "") {
        return;
    }
    isLoadingList.value = true;
    getQuery(origin, destination).then((data) => {
        list.value = data;
        isLoadingList.value = false;
    });
}

</script>
<template>
    <div class="container">
        <TopBar :isLoadingList="isLoadingList" />
        <Background :list="list" :search="search" />
    </div>
</template>
<style scoped>
.container {
    width: 90%;
    margin-top: 40px;
    display: flex;
    flex-direction: column;
}
</style>