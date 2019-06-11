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
        padding: ${this.styles.messagePaddingVertical} ${this.styles.messagePaddingHorizontal};
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
}
</style>