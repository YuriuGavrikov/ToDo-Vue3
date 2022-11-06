<script setup>
defineProps({
    task: Object
});
</script>

<template>
    <tr>
        <th scope="row" class="p-3">
            <input class="form-check-input" type="checkbox" value="" id="flexCheckDefault" v-model="task.checked" />
        </th>
        <td class="p-3">{{ task.name }}</td>
        <td class="p-3">{{ task.checked ? task.status[0] : task.status[1] }}</td>
        <td class="p-3">{{ task.date.toLocaleDateString('ru-RU') }}</td>
    </tr>
</template>

<style scoped>

</style>
