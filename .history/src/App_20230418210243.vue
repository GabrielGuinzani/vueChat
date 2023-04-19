<!-- <script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>

  <main>
    <TheWelcome />
  </main>
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
</style> -->


<template>
  <div id="chat-screen">
    <div class="titulo">
      <h2>Atendimento Online</h2>
    </div>
    <div class="messages-list" ref="messagesList">
      <div v-for="(message, index) in messages" :key="index" :class="[message.type === 'user' ? 'message-item2' : 'message-item']">
        <div class="msg-user" v-if="message.type === 'user'"><strong>{{ message.author }} diz:</strong></div>
        <div class="msg-chat">{{ message.text }}</div>
      </div>
    </div>
    <form id="form-chat-send" @submit.prevent="sendMessage">
      <input id="message" type="text" class="typebar" v-model="messageText" placeholder="Digite sua mensagem aqui">
      <button type="submit" class="botao">Enviar</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      messages: [],
      messageText: ''
    }
  },
  methods: {
    sendMessage() {
      const messageText = this.messageText.trim();
      if (messageText !== '') {
        this.messages.push({
          type: 'user',
          author: 'Você',
          text: messageText
        });
        this.messageText = '';
        this.$nextTick(() => {
          this.scrollToBottom();
        });
      }
    },
    scrollToBottom() {
      this.$refs.messagesList.scrollTop = this.$refs.messagesList.scrollHeight;
    }
  }
}
</script>
<style>
  #app {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    font-family: sans-serif;
  }

  .chat-container {
    border: 1px solid #ccc;
    border-radius: 5px;
    width: 400px;
    height: 500px;
    overflow-y: scroll;
    margin-bottom: 10px;
    padding: 10px;
  }

  .chat-message {
    display: flex;
    margin-bottom: 10px;
  }

  .chat-message img {
    width: 50px;
    height: 50px;
    border-radius: 50%;
    margin-right: 10px;
  }

  .chat-message .text {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: center;
  }

  .chat-message .text p {
    margin: 0;
    padding: 5px;
    background-color: #eee;
    border-radius: 5px;
  }

  #chat-input {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    width: 400px;
  }

  #chat-input input[type="text"] {
    width: 80%;
    padding: 5px;
    font-size: 16px;
    border: none;
    border-radius: 5px;
  }

  #chat-input button {
    width: 18%;
    height: 35px;
    background-color: #4285f4;
    border: none;
    border-radius: 5px;
    color: #fff;
    font-size: 16px;
    cursor: pointer;
  }
</style>
