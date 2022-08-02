<template>
  <div class="grid bg-slate-800 p-3 rounded-2xl">
    <h2 class="p-3 text-2xl text-stone-50 text-center">{{props.title}}</h2>
    <slot></slot>
  </div>
</template>

<script setup>
const props = defineProps({
  title:String,
});
</script>