<template>
  <h1>Bienvenue dans le {{ productsData.name }}</h1>
  <selection-box :selection="selection"></selection-box>
  <product-card
    v-for="(product, index) in productsData.products"
    :key="index"
    :product="product"
    @add-product="addProductToSelection"
  >
  </product-card>
</template>

<script>
import productsData from "../assets/data/product.json";
import ProductCard from "./ProductCard";
import SelectionBox from "./SelectionBox.vue";
export default {
  name: "product-list",
  components: {
    ProductCard,
    SelectionBox,
  },
  data() {
    return {
      productsData: productsData,
      selection: [],
    };
  },
  methods: {
    addProductToSelection(product) {
      this.selection.push(product);
      this.$emit("update-selection", product);
    },
  },
};
</script>

<style></style>
