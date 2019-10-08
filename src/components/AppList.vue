<template>
  <ul class="todos-container">
    <app-list-item @removeItem="removeItem(i)" v-for="(item, i) in items" :key="i" :text="item" />
  </ul>
</template>

<script>
import AppListItem from "@/components/AppListItem.vue";

export default {
  components: { AppListItem },
  props: ["items"],
  setup(props, { emit }) {
    function removeItem(index) {
      emit("removeItem", index);
    }

    return { removeItem };
  }
};
</script>

<style scoped>
.todos-container {
  list-style: none;
  padding: 0;
  margin: 0;
  margin-top: 3em;
}
</style>