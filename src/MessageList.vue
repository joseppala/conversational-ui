<template>
<div>
  <div class="message-list">
    <transition-group name="message-item-list" tag="div">
      <div
        class="message-container"
        :class="msg.type"
        v-for="(msg, i) in messages"
        :style="messageContainerStyle"
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
    </transition-group>
    <transition-group class="options-container" name="option-item-list" tag="div">
      <message-option
        v-for="(option, i) in options"
        :key="'option-' + i"
        :text="option.text"
        :styles="styles"
        @selected="$emit('optionSelected', option)">
      </message-option>
    </transition-group>
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
  computed: {
    messageContainerStyle() {
      return `margin-top: ${this.styles.messageMargin}`;
    }
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
        setTimeout(() => {
          this.scrollToEl(this.$refs['bottom-element']);
        }, 100);
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

.message-item-list-enter-active, .message-item-list-leave-active {
  transition: all .3s;
}
.SPINNER.message-item-list-leave-active {
  transition: none;
}
.message-item-list-enter {
  opacity: 0;
  transform: translateY(5px);
}
.message-item-list-leave-to {
  opacity: 0;
}

.option-item-list-enter-active {
  transition: opacity .3s;
}
.option-item-list-leave-active {
  transition: none;
}
.option-item-list-enter, .option-item-list-leave-to {
  opacity: 0;
}
</style>