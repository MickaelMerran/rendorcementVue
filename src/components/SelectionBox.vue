<template>
  <div>
    Ma selection : {{ selection.length }}
    <span v-if="nbrProduits">produits</span>
    <span v-else>produit</span>
  </div>
</template>

<script>
export default {
  name: "selection-box",
  props: ["selection"],
  computed: {
    nbrProduits() {
      if (this.selection.length > 1) {
        return true;
      }
      return false;
    },
  },
};
</script>

<style></style>
