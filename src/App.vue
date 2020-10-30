<template>
  <nav-bar @change-component="updateSelectedComponent"></nav-bar>

  <keep-alive>
    <component
      :is="selectedComponent"
      v-bind="currentProps"
      @update-selection="updateSelection"
      @delete-selection="deleteSelection"
    >
    </component>
  </keep-alive>
</template>

<script>
import ProductList from "./components/ProductList.vue";
import SelectionList from "./components/SelectionList.vue";

import NavBar from "./components/navigation/NavBar.vue";

export default {
  name: "App",
  components: {
    ProductList,
    NavBar,
    SelectionList,
  },
  data() {
    return {
      selectedComponent: "product-list",
      selectionArray: [],
    };
  },
  computed: {
    currentProps() {
      if (this.selectedComponent == "selection-list") {
        return { selection: this.selectionArray };
      }
      return false;
    },
  },
  methods: {
    updateSelectedComponent(comp) {
      this.selectedComponent = comp;
    },
    updateSelection(product) {
      this.selectionArray.push(product);
    },
    deleteSelection(product) {
      this.selectionArray.splice(product, 1);
    },
  },
};
</script>
<style></style>
