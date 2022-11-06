<script setup>
import { ref } from "vue"
let title = ref('')

const onSubmit = () => {
    if (title.value !== '') {
        emit('onAddTask', {
            id: Math.round(Math.random() * 100),
            checked: false,
            name: title.value,
            status: ['Выполнено', 'В работе'],
            date: new Date(),
        })
    }
    title.value = ''
}

const props = defineProps({
    showAdd: Boolean
});
const emit = defineEmits(['onAddTask', 'onShowAddChange'])
</script>

<template>
    <div class="bg-addTask" v-if="showAdd">
        <div class="addTask">
            <div class="modal-header">
                <h1 class="modal-title fs-5">Создать новую задачу</h1>
                <button @click="emit('onShowAddChange')" type="button" class="btn-close"></button>
            </div>
            <div class="modal-body">
                <div class="mb-3">
                    <label class="col-form-label">Описание:</label>
                    <input type="text" class="form-control" placeholder="Введите описание" v-model="title"
                        @keypress.enter="emit('onShowAddChange'), onSubmit()">
                </div>
            </div>
            <div class="modal-footer">
                <button type="button" class="btn btn-primary"
                    @click="emit('onShowAddChange'), onSubmit()">Создать</button>
            </div>
        </div>
    </div>
</template>

<style scoped>
.bg-addTask {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    z-index: 98;
    background: rgba(255, 255, 255, 0.01);
    backdrop-filter: blur(2px);
}

.addTask {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    z-index: 99;
    width: 400px;
    border: 1px solid #dde2e4;
    background: #fff;
    box-shadow: 0px 25px 50px -12px rgba(0, 0, 0, 0.25);
    border-radius: 6px;
    padding: 40px;
    display: flex;
    flex-direction: column;
}
</style>
