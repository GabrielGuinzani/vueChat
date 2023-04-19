<template>
    <form id="form-chat-send" @submit.prevent="sendMessage">
      <input v-model="message" type="text" id="message" name="message" placeholder="Digite sua mensagem..." class="typebar">
      <button type="submit" class="botao">ENVIAR</button>
    </form>
  </template>
  