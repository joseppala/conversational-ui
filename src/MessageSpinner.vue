<template>
<div class="message-spinner"
  :style="styles">
  <div class="dot dot1"></div>
  <div class="dot dot2"></div>
  <div class="dot dot3"></div>
</div>
</template>

<script>
export default {
  props: {
    styles: String
  }
}
</script>

<style scoped>
.message-spinner {
  text-align: center;
  transition: opacity 0.3s;
  opacity: 1;
  display: inline-block;
}
.dot {
  display: inline-block;
  width: 6px;
  height: 6px;
  margin: 0 2px;
  background-color: #888;
  border-radius: 100px;
  animation-iteration-count: infinite;
}
.dot1 {
  animation: spinner1 0.9s linear;
  animation-iteration-count: infinite;
}
.dot2 {
  animation: spinner2 0.9s linear;
  animation-iteration-count: infinite;
}
.dot3 {
  animation: spinner3 0.9s linear;
  animation-iteration-count: infinite;
}
@keyframes spinner1 {
  0% { opacity: 1; }
  25% { opacity: 0.4; }
  50% { opacity: 0.4; }
  75% { opacity: 0.4; }
  100% { opacity: 1; }
}
@keyframes spinner2 {
  0% { opacity: 0.4; }
  25% { opacity: 1; }
  75% { opacity: 1; }
  100% { opacity: 0.4; }
}
@keyframes spinner3 {
  0% { opacity: 0.4; }
  25% { opacity: 0.4; }
  50% { opacity: 1; }
  75% { opacity: 0.4; }
  100% { opacity: 0.4; }
}
</style>