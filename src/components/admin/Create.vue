<template>
    <div class="create">
        <h1>Add a Flight</h1>
        <input placeholder="origin" v-model="flight.origin" />
        <input placeholder="destination" v-model="flight.destination" />
        <input type="number" placeholder="flight number" v-model="flight.flightNumber" />
        <span>depart:</span>
        <input type="date" v-model="flight.depart" />
        <span>arrive:</span>
        <input type="date" v-model="flight.arrive" />
        <div class="nonstop">
            <div>nonstop:</div>
            <div><input type="checkbox" v-model="flight.nonstop" /></div>
        </div>
        <button @click="create">create flight</button>
    </div>
</template>

<script setup>
import { ref } from 'vue';

const props = defineProps({
    refresh: Function
})

const flight = ref({
    origin: "",
    destination: "",
    flightNumber: 0,
    depart: null,
    arrive: null,
    nonstop: false,
})

const addFlight = async (json) => {
    const res = await fetch("http://localhost:3000/flights", {
        method: "POST",
        headers: {
            'Content-Type': 'application/json'
        },
        body: JSON.stringify(json)
    });
    const data = await res.json();
    return data;
}

const empty = () => {
    flight.value.origin = "";
    flight.value.destination = "";
    flight.value.flightNumber = 0;
    flight.value.nonstop = false;
}

const create = () => {
    if (flight._rawValue.depart == null || flight._rawValue.arrive == null) {
        return;
    }
    addFlight(flight._rawValue).then(() => {
        props.refresh();
        empty();
    });
}

</script>

<style scoped lang="scss">
.create {
    font-size: 1.1em;
    font-family: Arial, Helvetica, sans-serif;
    margin: 10px;
    background-color: white;
    border: 1px solid grey;
    box-shadow: 2px 2px 2px;
    display: flex;
    flex-direction: column;
    align-items: left;
    justify-content: flex-start;
    width: 90%;
    padding: 5px;
    border-radius: 5px;

    input {
        width: 200px;
        border: 1px solid grey;
    }

    span {
        font-size: 0.9em;
        margin-top: 10px;
    }

    .nonstop {
        display: flex;
        flex-direction: row;
    }

    button {
        background-color: green;
    }
}
</style>