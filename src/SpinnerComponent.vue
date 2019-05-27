<template>
<div class="spinner">
  <div class="dot dot1"></div>
  <div class="dot dot2"></div>
  <div class="dot dot3"></div>
</div>
</template>

<style scoped>
.spinner {
  text-align: center;
  transition: opacity 0.3s;
  opacity: 1;
  border: 2px solid;
  border-radius: 8px;
  max-width: 85%;
  padding: 14px 16px;
  display: inline-block;
  background-color: #f4f4f4;
  border-color: #eeeeee;
  line-height: 6px;
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