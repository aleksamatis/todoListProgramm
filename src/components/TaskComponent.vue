<script setup>
import {ref} from 'vue';

const props = defineProps({
  task: Object,
})

const editable = ref(false);
const complited = ref(false);

function changeEditable() {
  editable.value = !editable.value
}

function changeCompleted() {
  props.task.completed = !props.task.completed
}
</script>
<template>
  <div class="main-container">
    <form>
      <p><label for="item">Введите свои планы:</label></p>
      <textarea id="item" name="itemlist" rows="4" cols="50" v-model="task.description" :disabled="!editable"></textarea>
      <br>
    </form>
    {{ task.completed }}
    <div class="images-container">
      <img src="@/assets/images/free-icon-check-mark-4225683.png"  @click="changeCompleted" :class="{inactive: !task.completed}"/>
      <img src="@/assets/images/icons8.png" @click="changeEditable" :class="{inactive: !editable}" />
    </div>
  </div>
</template>

<style scoped>
.main-container {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 2rem;
    gap: 2rem;
}
.images-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.inactive {
  opacity: 0.5;
}
</style>
