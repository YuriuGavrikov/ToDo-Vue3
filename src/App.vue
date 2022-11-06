<script setup>
import Header from "./components/Header.vue";
import SearchSort from "./components/SearchSort.vue";
import Table from "./components/Table.vue";
import AddTask from "./components/AddTask.vue";
import { ref, computed } from "vue"

const tasks = ref([
  {
    id: Math.round(Math.random() * 100),
    checked: true,
    name: 'Размещение новостей на сайте',
    status: ['Выполнено', 'В работе'],
    date: new Date("2022-04-22"),
  },
  {
    id: Math.round(Math.random() * 100),
    checked: false,
    name: 'Внедрить Wi-fi для читателей',
    status: ['Выполнено', 'В работе'],
    date: new Date("2022-03-25"),
  },
  {
    id: Math.round(Math.random() * 100),
    checked: true,
    name: 'Отредактировать раздел “Доступная среда”',
    status: ['Выполнено', 'В работе'],
    date: new Date("2022-03-15"),
  },
  {
    id: Math.round(Math.random() * 100),
    checked: false,
    name: 'Презентация “Информационные технологии”',
    status: ['Выполнено', 'В работе'],
    date: new Date("2022-03-15"),
  },
  {
    id: Math.round(Math.random() * 100),
    checked: false,
    name: 'Счётчики — внедрить дизайн',
    status: ['Выполнено', 'В работе'],
    date: new Date("2022-03-09"),
  },
  {
    id: Math.round(Math.random() * 100),
    checked: false,
    name: 'Сверстать новый layout',
    status: ['Выполнено', 'В работе'],
    date: new Date("2022-03-07"),
  },
  {
    id: Math.round(Math.random() * 100),
    checked: true,
    name: 'Скролл в новостях',
    status: ['Выполнено', 'В работе'],
    date: new Date("2022-03-01"),
  },
  {
    id: Math.round(Math.random() * 100),
    checked: false,
    name: 'Форма сброса пароля',
    status: ['Выполнено', 'В работе'],
    date: new Date("2022-02-25"),
  },
  {
    id: Math.round(Math.random() * 100),
    checked: true,
    name: 'Внедрение модуля Chat',
    status: ['Выполнено', 'В работе'],
    date: new Date("2022-02-20"),
  },
])

const search = ref('')
const sortBy = ref('')
const searchSortTasks = computed(() => {
  tasks.value.sort((a, b) => {
    if (sortBy.value === 'date') {
      if (Date.parse(a[sortBy.value]) > Date.parse(b[sortBy.value])) return -1
      if (Date.parse(a[sortBy.value]) < Date.parse(b[sortBy.value])) return 1
    }
    if (sortBy.value === 'checked') {
      if (a[sortBy.value] > b[sortBy.value]) return -1
      if (a[sortBy.value] < b[sortBy.value]) return 1
    }
  })
  return tasks.value.filter((task) => {
    return task.name.toLowerCase().includes(search.value.toLowerCase())
  })
})



const showAdd = ref(false);
const showAddChange = () => {
  showAdd.value = !showAdd.value;
}

const addTask = (item) => {
  tasks.value.push(item)
}
</script>

<template>
  <div class="container">
    <Header @onShowAddChange="showAddChange" />
    <SearchSort v-model:search="search" v-model:sortBy="sortBy" />
    <Table :tasks="tasks" :searchSortTasks="searchSortTasks" />
    <AddTask :showAdd="showAdd" @onAddTask="addTask" @onShowAddChange="showAddChange" />
  </div>
</template>

<style scoped>

</style>

