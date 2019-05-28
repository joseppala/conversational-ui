<template>
<div
  class="message-option"
  :style="styles"
  @click="$emit('selected')">
  {{text}}
</div>
</template>

<script>
export default {
  props: {
    text: String,
    styles: String
  },
}
</script>

<style scoped>
.message-option {
  display: inline-block;
}
</style>