<script lang="ts" setup>
import type { Task } from '../types';

const props = defineProps<{
  tasks: Task[]
}>();

const emits = defineEmits<{
  toggleDone: [id: string]
  removeTask: [id: string]
}>();

</script>

<template>
  <TransitionGroup name="list" tag="div">
    <article v-for="task in tasks" :key="task.id">
      <label>
        <input @input="emits('toggleDone', task.id)" :checked="task.done" type="checkbox">
        <span :class="{ done: task.done }">{{ task.title }}</span>
      </label>
      <button class="outline" @click="emits('removeTask', task.id)">Remove</button>
    </article>
  </TransitionGroup>
</template>

<style scoped>
article {
  margin-top: 1rem;
  display: flex;
  flex-direction: row;
  align-items: center;
}
.done {
  text-decoration: line-through;
}
button {
  display: flex;
  margin-left: auto;
}
.list-move,
.list-enter-active,
.list-leave-active {
  transition: all 0.5s ease;
}
.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateX(400px);
}
</style>
