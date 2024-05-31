<script setup lang="ts">
import BtnSubmit from './form/BtnSubmit.vue'
import InputText from './form/InputText.vue'
</script>

<template>
  <form action="">
    <InputText />
    <InputText />
    <BtnSubmit />
  </form>
</template>

<style scoped lang="scss">
form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}
</style>
