<script setup>
const props = defineProps({});
const emit = defineEmits(['onShowAddChange'])
</script>

<template>
    <nav class="navbar">
        <div class="container-fluid">
            <span class="mb-0 display-6">To do list</span>
            <button @click="emit('onShowAddChange')" type="button" class="btn btn-link">
                <i class="bi bi-plus-circle fs-2"></i>
            </button>
        </div>
    </nav>
</template>

<style scoped>

</style>
