<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
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

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
