<template>
<div>
  <message-list
    :messages="messages"
    :options="options"
    :styles="styles"
    @optionSelected="handleOptionSelect">
  </message-list>
</div>
</template>

<script>
import MessageList from './MessageList.vue';
import spinner from './spinnerMessage';

const OPTION_SHOW_DELAY = 500;
const DEFAULT_MESSAGE_DELAY = 500;
const NATURAL_REQUEST_DELAY = 300;
const TEXT_MESSAGE_CHAR_WRITE_DELAY = 10;
const TEXT_MESSAGE_CHAR_READ_DELAY = 30;

export default {
  components: {
    MessageList
  },
  props: {
    dialogue: Array,
    styles: Object,
    messageDelayMultiplier: Number
  },
  data() {
    return {
      initialDelay: 500,
      currentBranchIndex: 0,
      messages: [spinner],
      options: []
    };
  },
  methods: {
    handleOptionSelect(option) {
      this.showMessage({
        text: option.text,
        sender: 'USER',
        type: 'TEXT'
      });
      const branchIndex = this.dialogue.findIndex((branch) => branch.branchId === option.goto);
      this.run(branchIndex, 0);
    },
    removeSpinner() {
      const last = this.messages.length - 1;
      if (this.messages[last] && this.messages[last].type === 'SPINNER') {
        this.messages = this.messages.slice(0, last);
      }
    },
    showOptions(options) {
      this.removeSpinner();
      this.options = options;
    },
    showMessage(message) {
      this.removeSpinner();
      this.messages.push(message);
      this.options = [];
    },
    createMessage(node) {
      return Object.assign({
        sender: 'BOT'
      }, node);
    },
    calculateDelay(branch, nodeIndex) {
      let delay;
      const node = branch.nodes[nodeIndex];
      let minDelay = 0;
      if (nodeIndex > 0) {
        const prevNode = branch.nodes[nodeIndex - 1];
        if (prevNode.type === 'TEXT') {
          minDelay = prevNode.text.length * TEXT_MESSAGE_CHAR_READ_DELAY * this.messageDelayMultiplier;
        }
      }
      switch (node.type) {
        case 'OPTIONS': {
          delay = OPTION_SHOW_DELAY;
          break;
        }
        case 'TEXT': {
          delay = node.text.length * TEXT_MESSAGE_CHAR_WRITE_DELAY * this.messageDelayMultiplier;
          break;
        }
        default: {
          delay = DEFAULT_MESSAGE_DELAY;
        }
      }
      delay += NATURAL_REQUEST_DELAY;
      return delay > minDelay ? delay : minDelay;
    },
    run(branchIndex, nodeIndex) {
      const branch = this.dialogue[branchIndex];
      if (!branch) { return; }
      const node = branch.nodes[nodeIndex];
      if (!node) {
        this.$emit('end');
        return;
      }
      let cb;
      if (node.type === 'OPTIONS') {
        cb = () => {
          this.showOptions(node.options);
        }
      } else {
        cb = () => {
          this.showMessage(this.createMessage(node));
          this.run(branchIndex, nodeIndex + 1);
        }
      }
      setTimeout(() => {
        this.showMessage(spinner);
      }, NATURAL_REQUEST_DELAY);
      setTimeout(cb, this.calculateDelay(branch, nodeIndex));
    }
  },
  mounted() {
    setTimeout(() => {
      this.run(0, 0);
    }, this.initialDelay);
  }
}
</script>

<style>
</style>