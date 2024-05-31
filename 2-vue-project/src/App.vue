<script setup lang="ts">
import { RouterView } from 'vue-router'
import HeaderComponent from './components/header/HeaderComponent.vue'
</script>

<template>
  <div>
    <HeaderComponent />
    <RouterView />
  </div>
</template>

<style scoped lang="scss"></style>
