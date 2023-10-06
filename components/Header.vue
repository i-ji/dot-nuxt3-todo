<template>
  <div class="border-b border-[#ccc] flex justify-between pb-2">
    <h1 class="text-xl font-bold">Todos</h1>
    <button
      class="bg-gray-200 border border-black rounded-sm px-1 active:bg-gray-300"
      @click="purgeTodo"
    >
      Purge
    </button>
  </div>
</template>

<script setup lang="ts">
const emits = defineEmits(["purgeTodo"]);
const purgeTodo = () => {
  emits("purgeTodo");
};
</script>
