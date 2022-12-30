<template>
    <tr>
        <td><input v-model="element.origin" /></td>
        <td><input v-model="element.destination" /></td>
        <td><input v-model="element.flightNumber" /></td>
        <td>{{ convertDate(element.depart) }}</td>
        <td>{{ convertDate(element.arrive) }}</td>
        <td>{{ element.nonstop }}</td>
        <td><button class="update" @click="update(element)">go</button></td>
        <td><button class="delete" @click="remove(element.id)">go</button></td>
    </tr>
</template>

<script setup>
const props = defineProps({
    element: Object,
    refresh: Function
})

const convertDate = (date) => {
    const newDate = new Date(date);
    let year = newDate.getFullYear();
    let monthAux = newDate.getMonth() + 1;
    let month = (monthAux < 10) ? "0" + String(monthAux) : String(monthAux);
    let dayAux = newDate.getDate();
    let day = (dayAux < 10) ? "0" + String(dayAux) : String(dayAux);
    return `${day}/${month}/${year}`;
}

const removeFlight = async (id) => {
    const res = await fetch(`http://localhost:3000/flights/${id}`, { method: "DELETE" });
    const data = await res.json();
    return data;
}

const remove = (id) => {
    if (window.confirm('are you sure you want to delete this flight? ')) {
        removeFlight(id).then(() => {
            props.refresh();
        });
    }
}

const updateFlight = async (id, json) => {
    const res = await fetch(`http://localhost:3000/flights/${id}`, {
        method: "PATCH",
        headers: {
            'Content-Type': 'application/json'
        },
        body: JSON.stringify(json)
    });
    const data = await res.json();
    return data;
}

const update = (element) => {
    updateFlight(element.id, element).then(() => {
        props.refresh();
    });
}
</script>

<style>
.update {
    background-color: yellow;
}

.delete {
    background-color: red;
}
</style>