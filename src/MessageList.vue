<template>
<div>
  <div class="message-list">
    <div
      class="message-container"
      v-for="(msg, i) in messages"
      :key="'message-' + i">
      <message-text
        v-if="msg.type === 'TEXT' && msg.sender === 'USER'"
        :text="msg.text"
        :styles="styles.message + styles.messageUser">
      </message-text>
      <message-text
        v-if="msg.type === 'TEXT' && msg.sender === 'BOT'"
        :text="msg.text"
        :styles="styles.message + styles.messageBot">
      </message-text>
      <message-spinner
        v-if="msg.type === 'SPINNER'"
        :styles="styles.message + styles.messageBot">
      </message-spinner>
    </div>
    <div class="options-container">
      <message-option
        v-for="(option, i) in options"
        :key="'option-' + i"
        :text="option.text"
        :styles="styles.option"
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

export default {
  components: {
    MessageOption,
    MessageText,
    MessageSpinner
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