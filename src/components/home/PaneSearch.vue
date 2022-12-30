<script setup>
import { onMounted, ref } from "vue";
const origins = ref([]);
const destinations = ref([]);
const origin = ref("");
const destination = ref("");

const route = '/flights';
const url = "http://localhost:3000";

const getOrigins = async () => {
    const res = await fetch(url + route + "/cities/origins");
    const data = await res.json();
    return data;
}

const getDestinations = async () => {
    const res = await fetch(url + route + "/cities/destinations");
    const data = await res.json();
    return data;
}

onMounted(() => {
    getOrigins().then((data) => {
        origins.value = data
    });
    getDestinations().then((data) => {
        destinations.value = data
    });
});

defineProps({
    search: {
        type: Function
    }
})
</script>

<template>
    <div class="panesearch">
        <div class="boxsearch">
            <select v-model="origin">
                <option value="" disabled selected>from</option>
                <option v-for="element in origins" :key="'origin' + element.origin" :value="element.origin">{{
        element.origin
}}</option>
            </select>
        </div>
        <div class="boxsearch">
            <select v-model="destination">
                <option value="" disabled selected>to</option>
                <option v-for="element in destinations" :key="'destination' + element.destination"
                    :value="element.destination">{{ element.destination }}</option>
            </select>
        </div>
        <button @click="search(origin, destination)">Go</button>
    </div>
</template>

<style scoped lang="scss">
.panesearch {
    margin-top: 20px;
    width: 80%;
    height: 80%;
    display: flex;
    flex-direction: row;

    .boxsearch {
        display: flex;
        flex-direction: column;
        margin-right: 10px;
        position: relative;

        select {
            position: relative;
            right: 20px;
            background-color: white;
            box-shadow: 2px 2px 2px grey;
            width: auto;
            height: 25px;
            font-size: 20px;
        }
    }

    button {
        background-color: #415D65;
        border-radius: 5px;
        width: auto;
        font-size: 20px;
        color: white;
    }
}
</style>