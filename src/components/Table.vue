<script setup>
import ItemTable from "./ItemTable.vue"

const props = defineProps({
    tasks: Array,
    searchSortTasks: Array
});
</script>

<template>
    <table class="table">
        <thead>
            <tr>
                <th scope="col" class="p-3"></th>
                <th scope="col" class="col-10 p-3">Описание</th>
                <th scope="col" class="col-1 p-3">Статус</th>
                <th scope="col" class="p-3">Дата</th>
            </tr>
        </thead>
        <tbody>
            <ItemTable v-for="task in searchSortTasks" :task="task" />
        </tbody>
    </table>
</template>

<style scoped>

</style>
