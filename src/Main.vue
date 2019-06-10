<template>
<div :style="style">
  <dialogue
    :dialogue="dialogue"
    :styles="styles">
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
        messageTextColorBot: '#333333',
        messageBgColorBot: '#f4f4f4',
        messageBorderColorBot: '#eeeeee',
        messageTextColorUser: '#ffffff',
        messageBgColorUser: '#222222',
        messageBorderColorUser: '#222222',
        messageLinkColor: 'red',
        optionTextColor: '#333333',
        optionBgColor: '#ffffff',
        optionBorderColor: '#444444',
        containerMargin: '1rem',
        fontSize: '1rem'
      },
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
        margin: ${this.containerMargin};
        font-size: ${this.fontSize}rem;
      `;
    }
  }
}
</script>

<style>
</style>