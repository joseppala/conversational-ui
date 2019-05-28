<template>
<div
  class="message-text"
  :style="styles">
  {{text}}
</div>
</template>

<script>
export default {
  props: {
    text: String,
    styles: String
  }
}
</script>

<style scoped>
.message-text {
  max-width: 85%;
  display: inline-block;
}
</style>