<template>
  <button
    class="text-white font-bold py-0.5 px-2 border-b-4 rounded"
    :disabled="isDisabled"
  >
    {{ text }}
  </button>
</template>

<script>
export default {
  name: "base-button",
  props: ["text", "isDisabled"],
};
</script>

<style></style>
