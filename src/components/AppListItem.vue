<template>
  <li class="todo-item">
    <a
      :style="{ 'text-decoration': state.marked ? 'line-through' : 'none' }"
      class="item-text"
    >{{ text }}</a>
    <div class="item-controls">
      <button @click="removeItem" class="item-delete">✘</button>
      <button @click="markItem" class="item-complete">✓</button>
    </div>
  </li>
</template>

<script>
import { reactive } from "@vue/composition-api";

export default {
  props: ["text"],
  setup(props, { emit }) {
    const state = reactive({ marked: false });

    function markItem() {
      state.marked = !state.marked;
    }

    function removeItem() {
      emit("removeItem");
    }

    return {
      state,
      markItem,
      removeItem
    };
  }
};
</script>

<style scoped>
.todo-item {
  width: 100%;
  padding: 1em;
  background: #f4f4f4;
  margin: 10px auto;
  display: flex;
  justify-content: space-between;
  box-sizing: border-box;
}

.item-controls > button {
  margin: 0 2px;
}
</style>