<script lang="ts" setup>
import type { Task } from '../types';

const props = defineProps<{
  tasks: Task[]
}>();

</script>

<template>
  <article v-for="task in tasks" :key="task.id">
      {{ task.title }}
  </article>
</template>

<style scoped>
article {
  margin-top: 1rem;
}
</style>
