<template>
  <div id="app">
    <h1 class="title">My todo list</h1>
    <app-item-input @addItem="addItem" />
    <app-list @removeItem="removeItem" :items="state.items" />
  </div>
</template>

<script>
import { reactive } from "@vue/composition-api";
import AppList from "@/components/AppList.vue";
import AppItemInput from "@/components/AppItemInput.vue";

export default {
  name: "app",
  components: { AppList, AppItemInput },
  setup() {
    const state = reactive({
      items: []
    });

    const addItem = $event => state.items.unshift($event);
    const removeItem = $event => state.items.splice($event, 1);

    return {
      state,
      addItem,
      removeItem
    };
  }
};
</script>

<style>
#app {
  max-width: 400px;
  margin: 0 auto;
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

.title {
  text-align: center;
}
</style>
