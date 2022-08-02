<template>
  <CardTemplate :title="props.title">
    <ul role="list" class="divide-y divide-gray-200 bg-gray-400 rounded p-1.5">
      <li
        v-for="task in props.tasks"
        :key="task.id"
        class="py-4 flex justify-items-start place-content-between"
      >
        <Task :task="task" />
        <button
          v-show="inProgress"
          aria-label="delete item"
          class="text-white text-sm rounded bg-red-600"
          type="button"
          @click="$emit('deleteTask', task)"
        >
          X
        </button>
      </li>
    </ul>
    <div v-show="inProgress" class="flex">
      <input
        v-model="task"
        class="bg-gray-200 rounded-md mt-2 mr-1.5 px-3.5 text-slate-500 text-xs"
        type="text"
      />
      <input
        class="bg-gray-200 p-2 rounded-md mt-2 ml-1.5 py-1.5 px-3 text-slate-500 text-xs"
        type="button"
        value="Add"
        @click="$emit('saveTask', this.task), (this.task = null)"
      />
    </div>
  </CardTemplate>
</template>
<script setup>
import CardTemplate from "@/components/CardTemplate.vue";
import Task from "@/components/Task.vue";
import { ref } from "vue";

defineEmits(["saveTask", "deleteTask"]);

const task = ref(null);
const props = defineProps({
  tasks: Array,
  title: String,
  inProgress: {
    type: Boolean,
    default: true,
  },
});
</script>
