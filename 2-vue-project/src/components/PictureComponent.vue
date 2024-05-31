<script setup lang="ts">
import ReusableComponent from './ReusableComponent.vue'

const avatar = '/img/avatar.png'
const description = 'Kenny Steam'
</script>

<template>
  <div>
    <img :src="avatar" :alt="description" width="100" />
    <ReusableComponent />
    <ReusableComponent />
  </div>
</template>

<style lang="scss"></style>
