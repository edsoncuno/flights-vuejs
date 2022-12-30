<template>
    <div class="loading" v-if="isLoadingList">LOADING FLIGHTS, PLEASE WAIT</div>
    <div class="pane">
        <table>
            <thead>
                <tr>
                    <th>origin</th>
                    <th>destination</th>
                    <th>flight #</th>
                    <th>depart</th>
                    <th>arrive</th>
                    <th>nonstop</th>
                    <th>update</th>
                    <th>delete</th>
                </tr>
            </thead>
            <tbody>
                <Row v-for="element in list" :element="element" :refresh="refresh" />
            </tbody>
        </table>
    </div>
</template>

<script setup>
import Row from "./Row.vue";

defineProps({
    list: {
        type: Array
    },
    isLoadingList: {
        type: Boolean
    },
    refresh: Function
})
</script>

<style scoped lang="scss">
.loading {
    font-family: Arial, Helvetica, sans-serif;
    margin: 10px;
    background-color: #ddd;
    border: 1px solid grey;
    box-shadow: 2px 2px 2px;
    display: flex;
    flex-direction: column;
    align-items: left;
    justify-content: flex-start;
    width: 90%;
    padding: 5px;
    border-radius: 5px;
    background-color: white;
    color: red;
}

.pane {
    font-family: Arial, Helvetica, sans-serif;
    margin: 10px;
    background-color: #ddd;
    border: 1px solid grey;
    box-shadow: 2px 2px 2px;
    display: flex;
    flex-direction: column;
    align-items: left;
    justify-content: flex-start;
    width: 90%;
    padding: 5px;
    border-radius: 5px;
}
</style>