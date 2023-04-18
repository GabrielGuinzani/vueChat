<template>
    <div class="messages-list">
      <div v-for="(message, index) in messages" :key="index" class="message-item">
        <div class="msg-user"><strong>{{ message.user }} diz:</strong></div>
        <div class="msg-chat">{{ message.message }}</div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'MessageList',
    props: {
      messages: {
        type: Array,
        default: () => []
      }
    }
  }
  </script>