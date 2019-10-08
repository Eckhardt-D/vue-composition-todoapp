<template>
  <div class="input-container">
    <input placeholder="Enter a todo" v-model="state.text" type="text" id="vue3-add-item" />
    <input @click="addItem" type="submit" id="vue3-add-item-btn" value="add" />
  </div>
</template>

<script>
import { reactive, onMounted } from "@vue/composition-api";

export default {
  setup(props, { emit }) {
    const state = reactive({
      text: ""
    });

    function addItem() {
      if (state.text) emit("addItem", state.text);
      state.text = "";
    }

    return {
      state,
      addItem
    };
  }
};
</script>

<style scoped>
.input-container {
  text-align: center;
}

#vue3-add-item,
#vue3-add-item-btn {
  padding: 0.8em;
  font-size: 1.1em;
  font-weight: bolder;
}

#vue3-add-item-btn {
  cursor: pointer;
  padding-left: 1em;
  padding-right: 1em;
  margin-left: 8px;
  background: rgb(43, 43, 85);
  color: white;
  border-color: rgb(43, 43, 85);
  border-radius: 3px;
}

#vue3-add-item-btn:focus,
#vue3-add-item-btn:active {
  outline-color: salmon;
}
</style>