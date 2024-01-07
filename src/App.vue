<script setup>
  import { ref } from 'vue'
  const message = ref("Se puede pasar")
  const readMessage = () => {
    const utterance = new SpeechSynthesisUtterance()
    utterance.lang = 'es-AR'
    utterance.text = message.value
    speechSynthesis.speak(utterance)
  }
</script>

<template>
  <main>
    <h1>Portero</h1>
    <label for="msg">Mensaje a leer</label>
    <input v-model="message" id="msg" placeholder="se puede pasar" />
    <button @click="readMessage">Leer mensaje</button>
  </main>
</template>

<style scoped>
</style>
