<script setup>
import {ref, computed} from 'vue';
import TaskComponent from './TaskComponent.vue'
import Timer from './Timer.vue'

const tasks = ref([])

const newTask = ref({
  description: '',
  completed: false
})

function addNewTask() {
  tasks.value.push({...newTask.value})
  newTask.value = {description: '', completed: false}
}
const canAdd = computed(() => {
  return !!newTask.value.description
})


</script>

<template>
  <div class="main-container">
    <div>
      <TaskComponent :task="task" v-for="task in tasks"/>
      <TaskComponent :task="newTask" />
    </div>
    <button class="tasks-component-button" :class="{inactive: !canAdd}" @click="addNewTask" :disabled="!canAdd"><img src="@/assets/images/free-icon-plus-1828819.png" /></button>
    <Timer />
  </div>
  {{ canAdd }}
</template>
<style scoped>
  .main-container {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 2rem;
    gap: 2rem;
}

.tasks-component-button {
  background: none;
  border: 0;
}

.inactive {
  opacity: 0.5;
}
</style>
