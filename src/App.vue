<script setup lang="ts">
import GameHeader from './components/GameHeader.vue'
import GameFigure from './components/GameFigure.vue'
import GameWrongLetters from './components/GameWrongLetters.vue'
import GameWord from './components/GameWord.vue'
import GamePopup from './components/GamePopup.vue'
import GameNotification from './components/GameNotification.vue'
import { computed, ref } from 'vue'

const word = ref('василий')
const letters = ref<string[]>([])
const correctLetters = computed(() => letters.value.filter(x => word.value.includes(x)))
const wrongLetters = computed(() => letters.value.filter(x => !word.value.includes(x)))

window.addEventListener('keydown', ({ key }) => {
  // получаем символ кириллицы
  if(/[а-яА-ЯёЁ]/.test(key)) {
    letters.value.push(key.toLowerCase())
  }
})
</script>

<template>
  {{ word }}
  {{ letters }}
  {{ correctLetters }}
  {{ wrongLetters }}
  <GameHeader/>
  <div class="game-container">
    <GameFigure />
    <GameWrongLetters :wrong-letters="wrongLetters" />
    <GameWord :word="word" :correct-letters="correctLetters" />
  </div>

  <!-- Container for final message -->
  <GamePopup v-if="false" />

  <!-- Notification -->
  <GameNotification />
</template>