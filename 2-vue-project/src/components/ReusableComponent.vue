<script setup lang="ts">
import { ref } from 'vue'

const isActive = ref(false)

function handleActive() {
  isActive.value = !isActive.value
}
</script>

<template>
  <div>
    <button @click="handleActive">Clique aqui!</button>
    <span v-show="isActive">Ativado!</span>
  </div>
</template>

<style lang="scss"></style>
