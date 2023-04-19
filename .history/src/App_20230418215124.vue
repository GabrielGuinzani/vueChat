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

<!-- 
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
</template> -->

<template>
  <div id="chat-screen">
    <div class="titulo">
      <h2>Atendimento Online</h2>
    </div>
    <div class="messages-list" ref="messagesList">
      <div class="message-item message-fixed">
        <div class="msg-user"><strong>Atendente diz:</strong></div>
        <div class="msg-chat">Olá, como posso ajudar?</div>
      </div>
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
<!-- 
<style>
    html {
      box-sizing: border-box;
      font-size: 16px;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }

    *, *:before, *:after {
      box-sizing: inherit;
    }

    body, h1, h2, h3, h4, h5, h6, p, ol, ul {
      margin: 0;
      padding: 0;
      font-weight: normal;
    }

    ol, ul {
      list-style: none;
    }

    img {
      max-width: 100%;
      height: auto;
    }

    #form-chat-send {
      display: flex; 
      align-items: center; 
      margin-top: 20px;
    }

    .messages-list{
      margin: 15px 15px;
      padding-top: 15px;
      padding-bottom: 15px;
      overflow: auto;
      height: 400px;
    }

    /* width */
    ::-webkit-scrollbar {
      width: 8px;
    }

    /* Track */
    ::-webkit-scrollbar-track {
      background: #f1f1f1;
    }

    /* Handle */
    ::-webkit-scrollbar-thumb {
      background: #666;
      border-radius: 15px;
    }

    /* Handle on hover */
    ::-webkit-scrollbar-thumb:hover {
      background: #999;
    }

    body {
      font-family: Arial, sans-serif;
      background-color: #f9f9f9;
      margin: 0;
    }

    #chat-screen {
      max-width: 720px;
      margin: 5% auto 20px auto;
      padding: 20px;
      background-color: #fff;
      border-radius: 5px;
      box-shadow: 0 5px 10px rgba(0,0,0,.1);
    }

    .titulo {
      padding: 25px;
      display: flex;
      flex-direction: column;
      justify-content: center;
      text-align: center;
      margin-bottom: 20px;
      font-family: 'Segoe UI', Tahoma, Verdana, sans-serif;
      color: #666;
    }

    .titulo h2 {
      font-weight: bold;
      font-size: 24px;
    }

    .message-item {
      display: flex;
      flex-direction: column;
      margin-bottom: 20px;
      max-width: fit-content;
      margin-right: auto;
    }

    .message-item2 {
      display: flex;
      max-width: fit-content;
      flex-direction: column;
      justify-content: flex-end;
      margin-bottom: 20px;
      text-align: right;
      margin-left: auto;
      margin-right: 10px;
    }

    .msg-user {
      color: #666;
      font-size: 14px;
      margin-right: 10px;
      font-weight: bold;
      margin-bottom: 5px;
    }

    .msg-chat {
      background-color: #f1f1f1;
      padding: 10px;
      border-radius: 5px;
      font-size: 14px;
      overflow-wrap: break-word;
    }

    .typebar {
      flex: 1; 
      padding: 10px;
      border: none;
      border-bottom: 2px solid #ddd;
    }
    .botao {
      background-color: #4caf50;
      color: white;
      padding: 10px 20px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      font-size: 14px;
      margin-left: 10px; 
      transition: 0.6s;
  }
  
  .botao:hover {
      background-color: #3e8e41;
  }
  
  /* Adição para tornar a caixa do chat responsiva */
  @media only screen and (max-width: 768px) {
    #chat-screen {
      max-width: 90%;
    }
    
    .messages-list {
      height: 200px;
    }
  } -->
  #chat-screen {
    display: flex;
    flex-direction: column;
    height: 100vh;
    padding: 20px;
    box-sizing: border-box;
  }
  
  .titulo {
    text-align: center;
    margin-bottom: 20px;
  }
  
  .titulo h2 {
    font-size: 24px;
    font-weight: bold;
    color: #333;
    margin: 0;
  }
  
  .messages-list {
    flex: 1;
    overflow-y: auto;
  }
  
  .message-item {
    display: flex;
    margin-bottom: 10px;
  }
  
  .message-item2 {
    display: flex;
    margin-bottom: 10px;
    justify-content: flex-end;
  }
  
  .msg-user {
    font-weight: bold;
    margin-right: 10px;
  }
  
  .msg-chat {
    background-color: #f7f7f7;
    border-radius: 5px;
    padding: 10px;
  }
  
  .typebar {
    flex: 1;
    border: none;
    border-radius: 5px;
    padding: 10px;
    font-size: 16px;
    margin-right: 10px;
  }
  
  .botao {
    border: none;
    border-radius: 5px;
    background-color: #0077ff;
    color: #fff;
    padding: 10px;
    font-size: 16px;
    cursor: pointer;
    transition: background-color 0.3s ease-in-out;
  }
  
  .botao:hover {
    background-color: #005dff;
  }
  

