<template>
  <h1>Ma sélection</h1>
  <span v-if="selection.length == 0">
    <p>Vous n'avez pas sélectionné de produits</p>
  </span>
  <div v-else>
    <selection-card
      v-for="(product, index) in selection"
      :productIndex="index"
      :key="index"
      :product="product"
      @delete-product="deleteProductToSelection"
    >
      {{ product.name }}
    </selection-card>
    Total : {{ total }} €
  </div>
</template>

<script>
import SelectionCard from "./SelectionCard";

export default {
  name: "selection-list",
  components: {
    SelectionCard,
  },
  props: ["selection"],
  computed: {
    total() {
      var total = this.selection.reduce(function(previousValue, currentValue) {
        return previousValue.price + currentValue.price;
      });
      return total;
    },
  },
  methods: {
    deleteProductToSelection(product) {
      this.$emit("delete-selection", product);
    },
  },
};
</script>

<style></style>
