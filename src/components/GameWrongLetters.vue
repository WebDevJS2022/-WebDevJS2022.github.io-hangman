<script setup lang="ts">
interface Props {
  wrongLetters: string[]
}

defineProps<Props>()
</script>

<template>
  <div class="wrong-letters-container">
    <div class="wrong-letters">
      <p>Ошибки</p>
      <span>п , </span>
      <span>м , </span>
      <span>с </span>
    </div>
  </div>
</template>