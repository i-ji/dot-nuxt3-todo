<template>
  <div>
    <form @submit.prevent="addItem" class="flex gap-2 mt-4">
      <input
        type="text"
        class="flex flex-1 border border-black rounded-sm p-1"
        :value="modelValue"
        @input="$emit('update:modelValue', $event.target.value)"
      />
      <button
        class="bg-gray-200 border border-black rounded-sm px-1 active:bg-gray-300"
      >
        Add
      </button>
    </form>
  </div>
</template>

<script setup lang="ts">
const props = defineProps(["modelValue"]);
const emits = defineEmits(["addItem", "update:modelValue"]);
const addItem = () => {
  emits("addItem");
};
</script>
