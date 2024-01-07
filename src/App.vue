<script setup>
import { ref } from 'vue'
import Licenses from './components/licenses.vue'
const message = ref('Se puede pasar')
const readMessage = () => {
  const utterance = new SpeechSynthesisUtterance()
  utterance.lang = 'es-AR'
  utterance.text = message.value
  speechSynthesis.speak(utterance)
}
const shouldDisplayLicenses = ref(false)
const toggleLicenses = () => {
  shouldDisplayLicenses.value = !shouldDisplayLicenses.value
  console.log(shouldDisplayLicenses.value)
}
</script>

<template>
  <main>
    <h1>Portero</h1>
    <div class="field">
      <v-text-field
        color="primary"
        bg-color="white"
        id="msg-field"
        label="Mensaje a leer"
        v-model="message"
        placeholder="se puede pasar"
      />
    </div>
    <v-btn color="primary" @click="readMessage">Leer mensaje</v-btn>
    <v-btn variant="plain" class="btn" @click="toggleLicenses">Mostrar licencias</v-btn>
    <Licenses v-if="shouldDisplayLicenses" />
  </main>
</template>

<style scoped>
.field {
  width: 100%;
  padding: 1em;
}

main {
  background-image: url('assets/background.png');
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  width: 100vw;
  height: 100vh;
  overflow-y: scroll;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

h1 {
  color: white;
}

.btn {
  margin: 2em;
  color: white;
}
</style>
