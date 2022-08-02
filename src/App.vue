<template>
  <section v-if="inProgressTaskList()">
    <div class="grid bg-slate-800 p-3 rounded-2xl">
      <h2 class="p-3 text-2xl text-stone-50 text-center">In Progress Task List</h2>
      <TaskList :tasks="tasks.filter((t) => !t.completed)" />
    </div>
  </section>
  <section class="mt-2" v-if="completedTaskList()">
    <div class="grid bg-slate-800 p-3 rounded-2xl">
      <h2 class="p-3 text-2xl text-stone-50 text-center">Completed Task List</h2>
      <TaskList :tasks="tasks.filter((t) => t.completed)" />
    </div>
  </section>
</template>
<script setup>
import { ref } from "vue";
import TaskList from "@/components/TaskList.vue";

let tasks = ref([
  {
    id: 1,
    name: "Leer Clean Code",
    completed: false,
  },
  {
    id: 2,
    name: "Leer DDD",
    completed: true,
  },
  {
    id: 3,
    name: "Leer Harry Potter",
    completed: true,
  },
  {
    id: 4,
    name: "Pintar la Casa",
    completed: false,
  },
]);

function completedTaskList() {
  return this.tasks.filter((t) => t.completed).length;
}

function inProgressTaskList() {
  return this.tasks.filter((t) => !t.completed).length;
}
</script>
