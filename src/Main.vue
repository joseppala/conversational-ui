<template>
<div class="conversational-ui"
  :style="style">
  <dialogue
    :dialogue="dialogue"
    :styles="styles"
    :messageDelayMultiplier="messageDelayMultiplier">
  </dialogue>
</div>
</template>

<script>
import Dialogue from './Dialogue.vue';

export default {
  components: {
    Dialogue
  },
  data() {
    return {
      styles: {
        messageBorderWidth: '2px',
        messageBorderRadius: '8px',
        messageMargin: '10px',
        messagePaddingVertical: '10px',
        messagePaddingHorizontal: '16px',
        botMessageTextColor: '#333333',
        botMessageBgColor: '#f4f4f4',
        botMessageBorderColor: '#f4f4f4',
        userMessageTextColor: '#ffffff',
        userMessageBgColor: '#222222',
        userMessageBorderColor: '#222222',
        messageLinkColor: 'red',
        optionTextColor: '#333333',
        optionBgColor: '#ffffff',
        optionBorderColor: '#ffffff',
        optionBorderRadius: '1000px',
        optionBorderWidth: '0',
        optionPaddingVertical: '12px',
        optionPaddingHorizontal: '20px',
        optionBoxShadow: '0 2px 8px rgba(0, 0, 0, 0.3)',
        optionMargin: '10px',
        containerMarginVertical: '0',
        containerMarginHorizontal: '10px',
        fontSize: '1rem'
      },
      messageDelayMultiplier: 1,
      dialogue: [
        {
          branchId: "branch1",
          nodes: [
            {text: "Hello", type: "TEXT"},
            {text: "World!", type: "TEXT"},
            {type: 'OPTIONS', options: [
              {text: 'option1', goto: 'branch2'},
              {text: 'option2', goto: 'branch3'}
            ]}
          ]
        },
        {
          branchId: "branch2",
          nodes: [
            {text: "branch2", type: "TEXT"},
          ]
        },
        {
          branchId: "branch3",
          nodes: [
            {text: "branch3", type: "TEXT"},
          ]
        }
      ]
    };
  },
  computed: {
    style() {
      return `
        margin: ${this.styles.containerMarginVertical} ${this.styles.containerMarginHorizontal};
        font-size: ${this.styles.fontSize};
      `;
    }
  }
}
</script>

<style>
</style>