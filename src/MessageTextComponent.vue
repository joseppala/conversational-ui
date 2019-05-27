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
    sender: String
  },
  computed: {
    styles() {
      if (this.sender === 'USER') {
        return `
          float: right;
          background-color: #4baeff;
          color: #ffffff;
          border-color: #4baeff;
        `
      } else {
        return `
          background-color: #f4f4f4;
          color: #444444;
          border-color: #eeeeee;
        `
      }
    }
  }
}
</script>

<style scoped>
.message-text {
  border: 2px solid;
  border-radius: 8px;
  max-width: 85%;
  padding: 10px 16px;
  display: inline-block;
}
</style>