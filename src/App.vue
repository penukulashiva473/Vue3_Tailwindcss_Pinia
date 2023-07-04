<script setup></script>

<template>
  <header class="bg-gray-800 text-white py-4">
    <div class="container mx-auto">
      <h1 class="text-3xl">Website with Vue3 , TailwindCss and Pinia</h1>
    </div>
  </header>

  <main class="container mx-auto" style="height: 39rem">
    <div class="flex justify-center ...">
      <div class="grid gap-4 grid-flow-row auto-rows-max">
        <div>
          <h1 class="text-3xl py-4 text-green-900">
            Project with Vue3 , Tailwind and Pinia
          </h1>
        </div>
        <div v-for="task in taskStore.tasks" :key="task.id">
          <div class="grid gap-6 grid-flow-col auto-cols-4">
            <div>{{ task.id }}</div>
            <div>{{ task.title }}</div>
            <div>{{ task.isFav }}</div>
            <div>
              <button class="bg-red-500 text-white">delete</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>

  <footer class="bg-gray-800 text-white py-4">
    <div class="container mx-auto">
      <p>&copy; 2023 My Website. All rights reserved.</p>
    </div>
  </footer>
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
