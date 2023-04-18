<template>
    <form id="form-chat-send" @submit.prevent="sendMessage">
      <input v-model="message" type="text" id="message" name="message" placeholder="Digite sua mensagem..." class="typebar">
      <button type="submit" class="botao">ENVIAR</button>
    </form>
  </template>
  
  <script>
  var app = new Vue({
    el: '#chat-screen',
    data: {
      messages: [
        {
          author: 'Atendente',
          text: 'Olá, como posso ajudar?'
        }
      ],
      newMessage: ''
    },
    methods: {
      sendMessage: function() {
        if (this.newMessage.trim() === '') return;
        this.messages.push({author: 'Usuário', text: this.newMessage});
        this.newMessage = '';
      }
    }
  });
</script>

<style>

</style>