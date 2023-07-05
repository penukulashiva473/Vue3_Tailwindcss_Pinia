<template>
  <header class="bg-gray-800 text-white py-4">
    <div class="container mx-auto">
      <h1 class="text-3xl">Website with Vue3 , TailwindCss and Pinia</h1>
    </div>
  </header>

  <main class="container mx-auto" style="height: 39rem">
    <div class="grid gap-4 grid-flow-row auto-rows-max">
      <div class="grid grid-flow-col auto-cols-2">
        <div class="bg-blue-900" style="height: 39rem">
          <div class="flex justify-center items-center h-full">
            <img src="./assets/img.jpg" alt="Image" />
          </div>
        </div>
        <div class="bg-zinc-200 col-span-4 ...">
          <div class="flex justify-center ...">
            <div class="grid gap-4 grid-flow-row auto-rows-max">
              <div>
                <h1 class="text-3xl py-4 text-green-900">
                  Project with Vue3 , Tailwind and Pinia
                </h1>
              </div>
              <div class="text-pink-600">
                Total Count : {{ taskStore.totalCount }}
              </div>

              <div>
                <form @submit.prevent="handleSubmit">
                  <input
                    class="px-4 border border-indigo-600"
                    type="text"
                    placeholder="add ...    "
                    v-model="newTask"
                    style="width: 400px; height: 31px"
                  />
                  <button
                    class="bg-indigo-500 text-white rounded ml-5 p-1"
                    style="width: 100px"
                  >
                    Add
                  </button>
                </form>
              </div>

              <div
                v-for="task in taskStore.tasks"
                :key="task.id"
                class="border border-indigo-600 p-4"
              >
                <div class="grid gap-6 grid-flow-col auto-cols-3">
                  <div>{{ task.id }}</div>
                  <div>{{ task.title }}</div>

                  <div class="flex justify-end">
                    <button
                      class="bg-red-500 text-white"
                      @click="taskStore.deleteTask(task.id)"
                      style="width: 100px"
                    >
                      delete
                    </button>
                  </div>
                </div>
              </div>
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
import { ref } from "vue";

export default {
  setup() {
    const taskStore = useTaskStore();
    const newTask = ref("");
    const handleSubmit = () => {
      if (newTask.value.length > 0) {
        taskStore.addTask({
          title: newTask.value,
          isFav: false,
          id: Math.floor(Math.random() * 1000000),
        });
        newTask.value = "";
      }
    };

    return { taskStore, handleSubmit, newTask };
  },
};
</script>
<style scoped></style>
