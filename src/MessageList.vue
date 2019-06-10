<template>
<div>
  <div class="message-list">
    <div
      class="message-container"
      v-for="(msg, i) in messages"
      :key="'message-' + i">
      <message-text
        v-if="msg.type === 'TEXT'"
        :text="msg.text"
        :sender="msg.sender"
        :styles="styles">
      </message-text>
      <message-spinner
        v-if="msg.type === 'SPINNER'"
        :styles="styles">
      </message-spinner>
      <message-image
        v-if="msg.type === 'IMAGE'"
        :url="msg.url"
        @loaded="scrollToBottom">
      </message-image>
      <message-link
        v-if="msg.type === 'LINK'"
        :text="msg.text"
        :url="msg.url"
        :target="msg.target"
        :styles="styles">
      </message-link>
      <message-video-you-tube
        v-if="msg.type === 'VIDEO_YOUTUBE'"
        :video="msg.video">
      </message-video-you-tube>
    </div>
    <div class="options-container">
      <message-option
        v-for="(option, i) in options"
        :key="'option-' + i"
        :text="option.text"
        :styles="styles"
        @selected="$emit('optionSelected', option)">
      </message-option>
    </div>
    <div ref="bottom-element"></div>
  </div>
</div>
</template>

<script>
import MessageOption from './MessageOption.vue';
import MessageText from './MessageText.vue';
import MessageSpinner from './MessageSpinner.vue';
import MessageImage from './MessageImage.vue';
import MessageLink from './MessageLink.vue';
import MessageVideoYouTube from './MessageVideoYouTube.vue';

export default {
  components: {
    MessageOption,
    MessageText,
    MessageSpinner,
    MessageImage,
    MessageLink,
    MessageVideoYouTube
  },
  props: {
    messages: Array,
    options: Array,
    styles: Object
  },
  watch: {
    messages() {
      this.scrollToBottom();
    },
    options() {
      this.scrollToBottom();
    }
  },
  methods: {
    scrollToBottom() {
      this.$nextTick(() => {
        this.scrollToEl(this.$refs['bottom-element']);
      });
    },
    scrollToEl(el) {
      if (el.scrollIntoView) {
        el.scrollIntoView(false);
      }
    }
  }
}
</script>

<style scoped>
.options-container {
  margin: 30px 0 20px 0;
  text-align: center;
  overflow: hidden;
}
.message-container {
  position: relative;
  overflow: hidden;
}
</style>