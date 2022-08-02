<template>
  <ul role="list" class="divide-y divide-gray-200 bg-gray-400 rounded p-1.5">
    <li
      v-for="task in props.tasks"
      :key="task.id"
      class="py-4 flex justify-items-start place-content-between"
    >
      <Task :task="task" />
    </li>
  </ul>
</template>
<script setup>
import Task from "@/components/Task.vue";

const props = defineProps({
  tasks: Array,
});
</script>
