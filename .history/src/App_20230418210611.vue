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
  #chat-screen {
  width: 50%;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 500px;
}

  
  .titulo {
    margin-bottom: 20px;
    text-align: center;
  }
  
  .messages-list {
    height: 300px;
    overflow-y: auto;
    padding: 10px;
  }
  
  .message-item {
    margin: 10px;
    padding: 10px;
    background-color: #eee;
    border-radius: 5px;
  }
  
  .message-item2 {
    margin: 10px;
    padding: 10px;
    background-color: #b3d9ff;
    border-radius: 5px;
  }
  
  .msg-user {
    font-weight: bold;
    margin-bottom: 5px;
  }
  
  .typebar {
    border: none;
    border-radius: 5px;
    box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.1);
    margin-right: 10px;
    padding: 10px;
    width: calc(100% - 90px);
  }
  
  .botao {
    background-color: #0077c2;
    border: none;
    border-radius: 5px;
    box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.3);
    color: #fff;
    font-weight: bold;
    padding: 10px;
    width: 80px;
  }
  
  .botao:hover {
    background-color: #0061a7;
    cursor: pointer;
  }
  
  #form-chat-send {
    display: flex;
    justify-content: center;
    margin-top: 20px;
  }
</style>
