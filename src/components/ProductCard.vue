<template>
  <div
    class="border border-black m-2 p-2 rounded flex justify-between"
    :class="isStockClass"
  >
    <div>
      <h3 class="text-lg font-bold">{{ productName }} ({{ product.price }})</h3>
      <p>{{ product.categorie }}</p>
    </div>
    <base-button
      text="Sélectionner"
      @click="addToSelection"
      :isDisabled="productStock"
      :class="isDisabledClass"
    >
    </base-button>
  </div>
</template>

<script>
export default {
  name: "product-card",
  props: ["product"],
  computed: {
    productName() {
      if (this.product.name.split(".").length > 1) {
        return this.product.name.split(".")[1];
      }
      return this.product.name;
    },

    productStock() {
      if (this.product.stock == "out") {
        return true;
      }
      return false;
    },

    isStockClass() {
      return {
        "bg-red-300": this.productStock,
        "bg-green-300": !this.productStock,
      };
    },
    isDisabledClass() {
      return {
        "bg-gray-500 hover:bg-red-400  border-gray-700 hover:border-red-500  ": this
          .productStock,
        "bg-blue-500 hover:bg-blue-400  border-blue-700 hover:border-blue-500 ": !this
          .productStock,
      };
    },
  },
  methods: {
    addToSelection() {
      this.$emit("add-product", this.product);
    },
  },
};
</script>

<style scoped></style>
