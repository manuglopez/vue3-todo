<template>
  <section v-if="inProgressTaskList()">
    <TaskList
        :tasks="tasks.filter((t) => !t.completed)"
        :title="'In Progress Task List'"
        @save-task="addTask"
    />
  </section>
  <section class="mt-2" v-if="completedTaskList()">
    <TaskList
      :tasks="tasks.filter((t) => t.completed)"
      :title="'Completed Task List'"
      :in-progress="false"
    />
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

function addTask(name) {
  tasks.value.push({
    id:tasks.value.length++,
    name:name,
    completed:false
  })
}
function completedTaskList() {
  return this.tasks.filter((t) => t.completed).length;
}

function inProgressTaskList() {
  return this.tasks.filter((t) => !t.completed).length;
}
</script>
