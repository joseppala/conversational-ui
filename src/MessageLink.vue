<template>
<div class="message-link"
  :style="containerStyles">
  <a :href="url"
    :target="target || '_blank'"
    :style="linkStyles">
    {{text}}
  </a>
</div>
</template>

<script>
export default {
  props: {
    text: String,
    url: String,
    target: String,
    linkStyles: String,
    containerStyles: String
  }
}
</script>

<style scoped>
.message-link {
  max-width: 85%;
  display: inline-block;
}
</style>