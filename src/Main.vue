<template>
<div>
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
        message: `
          border: 2px solid;
          border-radius: 8px;
          padding: 12px 16px;
          font-size: 1rem;
          margin: 10px 10px 0 10px;
        `,
        messageBot: `
          color: #333333;
          border-color: #eeeeee;
          background-color: #f4f4f4;
        `,
        messageUser: `
          color: #ffffff;
          border-color: #222222;
          background-color: #222222;
          float: right;
        `,
        option: `
          border-radius: 1000px;
          border: 2px solid #444444;
          padding: 12px 20px;
          margin: 10px;
          font-weight: normal;
          color: #333333;
          background-color: #ffffff;
        `,
        image: `
          margin: 10px 10px 0 10px;
        `
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
  }
}
</script>

<style>
</style>