<template>
<div>
  <div class="message-list">
    <div
      class="message-container"
      v-for="(msg, i) in messages" :key="i">
      <message-text-component
        v-if="msg.type === 'TEXT'"
        :text="msg.text"
        :sender="msg.sender">
      </message-text-component>
      <spinner-component
        v-if="msg.type === 'SPINNER'">
      </spinner-component>
    </div>
    <div class="options-container">
      <option-component
        v-for="(option, i) in options" :key="i"
        :text="option.text"
        @selected="$emit('optionSelected', option)">
      </option-component>
    </div>
  </div>
</div>
</template>

<script>
import OptionComponent from './OptionComponent.vue';
import MessageTextComponent from './MessageTextComponent.vue';
import SpinnerComponent from './SpinnerComponent.vue';

export default {
  components: {
    OptionComponent,
    MessageTextComponent,
    SpinnerComponent
  },
  props: {
    messages: Array,
    options: Array
  },
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
  margin: 10px;
  overflow: hidden;
}
</style>