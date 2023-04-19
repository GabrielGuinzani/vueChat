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
    <div class="messages-list" id="conversa">

  </div>
    <div class="messages-list" ref="messagesList">
      <div v-for="(message, index) in messages" :key="index" :class="[message.type === 'user' ? 'message-item2' : 'message-item']">
        <div class="msg-user" v-if="message.type === 'user'"><strong>{{ message.author }} diz:</strong>
        </div>
        <div class="msg-chat">{{ message.text }}
        </div>
  
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
<!-- 
<style>
body {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 600px;
}

#app {
  width: 800px;
  height: 600px;
}   

#chat-screen {
  width: 500px;
  height: 600px;
  margin: 0 auto;
  border: 1px solid #ccc;
  background-color: #fff;
  padding: 20px;
  display: flex;
  flex-direction: column;
}

.titulo {
  text-align: center;
  font-size: 24px;
  margin-bottom: 20px;
  color: gray;
}

.messages-list {
  flex: 1;
  overflow-y: auto;
}

.message-item {
  background-color: #f2f2f2;
  border-radius: 5px;
  padding: 10px;
  margin-bottom: 10px;
  color: gray;
}

.message-item2 {
  background-color: #e6f7ff;
  border-radius: 5px;
  padding: 10px;
  margin-bottom: 10px;
  color: gray;
}

.msg-user {
  margin-bottom: 5px;
  color: gray;
}

.msg-chat {
  color: gray;
}

.typebar {
  width: 100%;
  padding: 10px;
  border: none;
  border-bottom: 1px solid #ccc;
  margin-right: 10px;
  font-size: 16px;
  color: gray;
}

.botao {
  background-color: #4CAF50;
  color: #fff;
  border: none;
  border-radius: 5px;
  padding: 10px;
  margin-top: 10px;
  cursor: pointer;
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
</style> -->

<style>
  #chat-screen {
    margin: auto;
    max-width: 500px;
    height: 500px;
    background-color: #fff;
    border-radius: 10px;
    box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
    overflow: hidden;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }

  .titulo {
    background-color: #4CAF50;
    color: #fff;
    font-size: 20px;
    text-align: center;
    padding: 10px;
    border-top-left-radius: 10px;
    border-top-right-radius: 10px;
  }

  .messages-list {
    padding: 10px;
    overflow-y: scroll;
    flex-grow: 1;
  }

  .message-item {
    display: flex;
    flex-direction: row;
    margin: 5px 0;
  }

  .message-item2 {
    display: flex;
    flex-direction: row-reverse;
    margin: 5px 0;
  }

  .msg-user {
    font-weight: bold;
    margin-right: 5px;
    color: gray;
  }

  .msg-chat {
    border-radius: 5px;
    padding: 10px;
    background-color: #eee;
    color: gray;
    max-width: 70%;
    word-wrap: break-word;
  }

  #form-chat-send {
    display: flex;
    flex-direction: row;
    padding: 10px;
  }

  .typebar {
    flex-grow: 1;
    padding: 10px;
    border: none;
    border-bottom: 1px solid #ddd;
  }

  .botao {
    background-color: #4CAF50;
    color: #fff;
    border: none;
    border-radius: 5px;
    padding: 10px;
    cursor: pointer;
    margin-left: 10px;
  }
</style>


