<template>
  <div>
    <Header @click="purgeTodo"></Header>
    <ul>
      <li
        class="flex justify-between items-start mt-4"
        v-for="(todo, index) in todos"
        :key="todo"
      >
        <label
          ><input
            type="checkbox"
            class="mr-2"
            v-model="todo.isCompleted"
          /><span :class="{ completeTodo: todo.isCompleted }">{{
            todo.title
          }}</span>
        </label>
        <button
          class="bg-gray-200 border border-black rounded-sm px-2 active:bg-gray-300 ml-1"
          @click="deleteItem(index)"
        >
          x
        </button>
      </li>
    </ul>
    <Form v-model="newItem" @addItem="addItem"></Form>
  </div>
</template>

<style>
.completeTodo {
  color: #aaa;
  text-decoration: line-through;
}
</style>

<script setup lang="ts">
const props = defineProps(["todos"]);
let newItem = ref<string>("");
const todos = useCookie("todos", {
  default: () => [] as object[],
});

const addItem = () => {
  if (newItem.value === "") return;

  let todo = {
    title: newItem.value,
    isCompleted: false,
  };
  todos.value.push(todo);
  newItem.value = "";
};

const deleteItem = (index: number) => {
  if (confirm("Are you sure?")) {
    todos.value.splice(index, 1);
  }
};

const purgeTodo = () => {
  todos.value = [];
};
</script>
