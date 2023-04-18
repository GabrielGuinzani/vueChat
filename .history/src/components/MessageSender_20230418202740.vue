<template>
  <div id="chat-screen">
    <header>
      <div class="titulo">
        <h2>ATENDIMENTO ONLINE</h2>
      </div>
    </header>
    <MessageList :messages="messages" />
    <MessageForm @message-sent="handleMessageSent" />
  </div>
</template>

<script>
import MessageList from './MessageList.vue'
import MessageForm from './MessageForm.vue'

export default {
  name: 'ChatScreen',
  components: {
    MessageList,
    MessageForm,
  },
  data() {
    return {
      messages: [
        { user: 'Atendente', message: 'Olá, como posso ajudar?' }
      ]
    }
  },
  methods: {
    handleMessageSent(message) {
      this.messages.push({ user: 'Usuário', message })
    }
  }
}
</script>