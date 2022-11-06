<script setup>
const emit = defineEmits(['update:search', 'update:sortBy'])
const props = defineProps({
    tasks: Array,
    search: String,
    sortBy: String
});
</script>

<template>
    <div class="d-flex align-items-center">
        <i class="bi bi-search text-primary"></i>
        <div class="p-2 flex-grow-1">
            <input @input="$emit('update:search', $event.target.value)" type="text" class="form-control"
                placeholder="Поиск">
        </div>
        <span>Сортировать по:</span>
        <div class="p-2 flex-shrink-1">
            <select :value="sortBy" @input="$emit('update:sortBy', $event.target.value)" class="form-select">
                <option value="date">Дата</option>
                <option value="checked">Статус</option>
            </select>
        </div>
    </div>
</template>

<style scoped>

</style>
