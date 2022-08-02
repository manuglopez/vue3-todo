<template>
  <section v-show="inProgressTaskList()">
    <TaskList
      :tasks="tasks.filter((t) => !t.completed)"
      :title="'In Progress Task List'"
      @save-task="addTask"
      @delete-task="deleteTask"
    />
  </section>
  <section class="mt-2" v-show="completedTaskList()">
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

function deleteTask(task) {
  console.log(task);
  for (let i = 0; i < tasks.value.length; i++) {
    if (tasks.value[i] === task) {
      tasks.value.splice(i, 1);
    }
  }
  console.log(tasks.value);
}
function addTask(name) {
  tasks.value.push({
    id: tasks.value.length++,
    name: name,
    completed: false,
  });
}
function completedTaskList() {
  return this.tasks.filter((t) => t.completed).length;
}

function inProgressTaskList() {
  return this.tasks.filter((t) => !t.completed).length;
}
</script>
