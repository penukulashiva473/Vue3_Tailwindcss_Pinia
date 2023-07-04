<script setup></script>

<template>
  <header class="bg-gray-800 text-white py-4">
    <div class="container mx-auto">
      <h1 class="text-3xl">Website with Vue3 , TailwindCss and Pinia</h1>
    </div>
  </header>

  <main class="container mx-auto" style="height: 39rem">
    <div class="flex justify-center ...">
      <h1 class="text-3xl py-4">Project with Vue3 , Tailwind and Pinia</h1>
    </div>
  </main>

  <footer class="bg-gray-800 text-white py-4">
    <div class="container mx-auto">
      <p>&copy; 2023 My Website. All rights reserved.</p>
    </div>
  </footer>

  <!-- {{ taskStore.name }}

  <div v-for="task in taskStore.tasks" :key="task.id">
    <p>{{ task.title }}</p>
  </div> -->
</template>

<script>
import { useTaskStore } from "./stores/TaskStore";

export default {
  setup() {
    const taskStore = useTaskStore();

    return { taskStore };
  },
};
</script>
<style scoped></style>
