<template>
<div
  class="message-text"
  :style="style">
  {{text}}
</div>
</template>

<script>
export default {
  props: {
    text: String,
    sender: String,
    styles: Object
  },
  computed: {
    style() {
      let styl = `
        border: ${this.styles.messageBorderWidth} solid;
        border-radius: ${this.styles.messageBorderRadius};
        padding: ${this.styles.messagePaddingVertical} ${this.styles.messagePaddingHorizontal};
      `;
      if (this.sender === 'USER') {
        styl += `
          float: right;
          color: ${this.styles.userMessageTextColor};
          border-color: ${this.styles.userMessageBorderColor};
          background-color: ${this.styles.userMessageBgColor};
        `;
      } else {
        styl += `
          color: ${this.styles.botMessageTextColor};
          border-color: ${this.styles.botMessageBorderColor};
          background-color: ${this.styles.botMessageBgColor};
        `;
      }
      return styl;
    }
  }
}
</script>

<style scoped>
.message-text {
  max-width: 85%;
  display: inline-block;
}
</style>