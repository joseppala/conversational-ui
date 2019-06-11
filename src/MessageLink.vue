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
    styles: Object
  },
  computed: {
    containerStyles() {
      return `
        border: ${this.styles.messageBorderWidth} solid;
        border-radius: ${this.styles.messageBorderRadius};
        border-color: ${this.styles.botMessageBorderColor};
        background-color: ${this.styles.botMessageBgColor};
      `;
    },
    linkStyles() {
      return `color: ${this.styles.messageLinkColor}`
    }
  }
}
</script>

<style scoped>
.message-link {
  max-width: 85%;
  display: inline-block;
  padding: 10px 16px;
  margin: 10px 10px 0 10px;
}
</style>