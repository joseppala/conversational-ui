<template>
<div
  class="message-video"
  ref="container">
</div>
</template>

<script>
export default {
  props: {
    video: String
  },
  mounted() {
    this.$nextTick(() => {
      const dim = this.$refs.container.getBoundingClientRect();
      const width = Math.floor(dim.width);
      const height = Math.round(width / 1.5);
      const html = `<iframe width="${width}" height="${height}"
        src="https://www.youtube.com/embed/${this.video}"
        frameborder="0"
        allowfullscreen>
        </iframe>`;
      this.$refs.container.innerHTML = html;
    });
  }
}
</script>

<style scoped>
.message-video {
  width: 85%;
  display: inline-block;
}
</style>