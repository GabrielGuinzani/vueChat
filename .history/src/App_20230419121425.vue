
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

<style>
body {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 700px;
  width: 50%;
  margin: auto;
}

#chat-screen {
  width: 100%;
  height: inherit;
  margin: 0 auto;
  border: 1px solid #ccc;
  background-color: #fff;
  padding: 20px;
  display: flex;
  flex-direction: column;
  overflow-y: auto;
}

.titulo {
  text-align: center;
  font-size: 24px;
  margin-bottom: 20px;
  color: rgb(75, 72, 72);
}

.messages-list {
  flex: 1;
  overflow-y: auto;
  width: inherit;
  height: 500px;
}

.message-item {
  background-color: #f2f2f2;
  border-radius: 5px;
  padding: 10px;
  margin-bottom: 10px;
  color: rgb(75, 72, 72);
  text-align: left;
  width: max-content
}

.message-item2 {
  background-color: #e0f7e0;
  border-radius: 5px;
  padding: 10px;
  margin-bottom: 10px;
  color: rgb(75, 72, 72);
  text-align: end;
  width: min-content
}

.msg-user {
  margin-bottom: 5px;
  color: rgb(75, 72, 72);
  
}

.msg-chat {
  color: rgb(75, 72, 72);
}

.typebar {
  width: 100%;
  padding: 10px;
  border: none;
  border-bottom: 1px solid #ccc;
  margin-right: 10px;
  font-size: 16px;
  color: rgb(75, 72, 72);
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
    background-color: #0b4e27;
    cursor: pointer;
  }
  
  #form-chat-send {
    display: flex;
    justify-content: center;
    margin-top: 20px;
  }
</style>