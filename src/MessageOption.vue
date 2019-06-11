<template>
<div
  class="message-option"
  :style="style"
  @click="$emit('selected')">
  {{text}}
</div>
</template>

<script>
export default {
  props: {
    text: String,
    styles: Object
  },
  computed: {
    style() {
      return `
        border: ${this.styles.optionBorderWidth} solid;
        border-radius: ${this.styles.optionBorderRadius};
        color: ${this.styles.optionTextColor};
        border-color: ${this.styles.optionBorderColor};
        background-color: ${this.styles.optionBgColor};
        padding: ${this.styles.optionPaddingVertical} ${this.styles.optionPaddingHorizontal};
        margin: ${this.styles.optionMargin};
      `
    }
  }
}
</script>

<style scoped>
.message-option {
  display: inline-block;
  font-weight: normal;
}
</style>