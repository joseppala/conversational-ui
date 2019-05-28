<template>
<div
  class="message-image"
  :style="styles">
  <img
    :src="url"
    @load="$emit('loaded')" />
</div>
</template>

<script>
export default {
  props: {
    url: String,
    styles: String
  }
}
</script>

<style scoped>
.message-image {
  max-width: 85%;
  display: inline-block;
}
.message-image img {
  max-width: 100%;
  border-radius: 8px;
}
</style>