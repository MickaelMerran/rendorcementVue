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
      class=" bg-red-500 hover:bg-red-400  border-red-700 hover:border-red-500"
      text="Supprimer"
      @click="deleteProduct"
    >
    </base-button>
  </div>
</template>

<script>
export default {
  name: "selection-card",
  props: ["product", "productIndex"],
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
  },
  methods: {
    deleteProduct() {
      this.$emit("delete-product", this.productIndex);
    },
  },
};
</script>

<style scoped></style>
