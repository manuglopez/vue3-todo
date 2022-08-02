<template>
  <CardTemplate :title="props.title">
    <ul role="list" class="divide-y divide-gray-200 bg-gray-400 rounded p-1.5">
      <li
        v-for="task in props.tasks"
        :key="task.id"
        class="py-4 flex justify-items-start place-content-between"
      >
        <Task :task="task" />
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
        @click="$emit('saveTask', this.task)"
      />
    </div>
  </CardTemplate>
</template>
<script setup>
import CardTemplate from "@/components/CardTemplate.vue";
import Task from "@/components/Task.vue";
import { ref } from "vue";

defineEmits(["saveTask"]);

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
