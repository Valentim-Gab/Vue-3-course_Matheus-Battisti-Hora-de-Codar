<script setup lang="ts">
defineEmits(['handleChangePicture'])
</script>

<template>
  <button @click="$emit('handleChangePicture')">Trocar imagem de perfil</button>
</template>

<style lang="scss"></style>
