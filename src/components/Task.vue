<template>
  <div class="ml-3 flex justify-between space-x-4">
    <label
      :class="props.task.completed ? 'line-through text-blue-100' : ''"
      class="text-sm font-medium text-white"
    >
      {{ props.task.name }}
      <input
        type="checkbox"
        :id="props.task.id"
        v-model="props.task.completed"
      />
    </label>
  </div>
</template>

<script setup>
const props = defineProps({
  task: JSON,
});
</script>
