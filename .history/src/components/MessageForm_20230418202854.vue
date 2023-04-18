<template>
    <form id="form-chat-send" @submit.prevent="handleSubmit">
      <input v-model="message" type="text" id="message" name="message" placeholder="Digite sua mensagem..." class="typebar">
      <button type="submit" class="botao">ENVIAR</button>
    </form>
  </template>
  
  <script>
  export default {
    name: 'MessageForm',
    data() {
      return {
        message: ''
      }
    },
    methods: {
      handleSubmit() {
        if (this.message.trim().length > 0) {
          this.$emit('message-sent', this.message.trim())
          this.message = ''
        }
      }
    }
  }
  </script>