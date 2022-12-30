<script setup>
defineProps({
    list: {
        type: Array
    }
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

</script>

<template>
    <div class="paneflights">
        <div class="head">
            <div class="cell"> Flight # </div>
            <div class="cell"> Departs </div>
            <div class="cell"> Arrives </div>
            <div class="cell"> Nonstop </div>
        </div>
        <div v-for="(element) in list" :key="element.id" class="row">
            <div class="cell">{{ element.flightNumber }}</div>
            <div class="cell">{{ convertDate(element.depart) }}</div>
            <div class="cell">{{ convertDate(element.arrive) }}</div>
            <div class="cell">{{ String(element.nonstop) }}</div>
        </div>
        <div v-if="list.length == 0">-- no flights found --</div>
    </div>
</template>

<style scoped lang="scss">
.paneflights {
    margin-top: 10px;
    background-color: white;
    width: 80%;
    height: 80%;
    padding: 20px;

    .head {
        display: flex;
        flex-direction: row;
        border-bottom: 1px solid #ccc;
        width: 100%;
    }

    .row {
        display: flex;
        flex-direction: row;
    }

    .cell {
        flex: 1;
    }
}
</style>