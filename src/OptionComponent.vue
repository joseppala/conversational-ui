<template>
<div
  class="option"
  @click="$emit('selected')">
  {{text}}
</div>
</template>

<script>
export default {
  props: {
    text: String
  },
}
</script>

<style scoped>
.option {
  display: inline-block;
  padding: 10px 20px;
  margin: 10px;
  border-radius: 1000px;
  border: 2px solid #4baeff;
}
</style>