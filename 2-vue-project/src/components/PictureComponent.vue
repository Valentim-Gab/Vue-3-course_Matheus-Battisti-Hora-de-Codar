<script setup lang="ts">
import { ref } from 'vue'
import BtnChangePicture from './BtnChangePicture.vue'

const avatar = ref('/img/avatar.png')
const description = 'Kenny Steam'

function handleChangeImage() {
  avatar.value =
    avatar.value == '/img/avatar.png'
      ? (avatar.value = '/img/avatar2.png')
      : (avatar.value = '/img/avatar.png')
}
</script>

<template>
  <div>
    <img :src="avatar" :alt="description" width="100" />
    <BtnChangePicture @handle-change-picture="handleChangeImage" />
  </div>
</template>

<style lang="scss"></style>
