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
        border: ${this.styles.messageBorderWidth} solid;
        border-radius: 1000px;
        color: ${this.styles.optionTextColor};
        border-color: ${this.styles.optionBorderColor};
        background-color: ${this.styles.optionBgColor};
      `
    }
  }
}
</script>

<style scoped>
.message-option {
  display: inline-block;
  border-radius: 1000px;
  padding: 10px 20px;
  margin: 10px;
  font-weight: normal;
}
</style>