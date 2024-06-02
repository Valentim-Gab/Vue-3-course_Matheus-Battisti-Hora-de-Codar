<script setup lang="ts">
import { RouterView } from 'vue-router'
import NavBar from '@/components/header/NavBar.vue'
import FooterComponent from '@/components/FooterComponent.vue'

const logoSrc = '/img/logo.png'
const appName = 'Make Your Burger'
</script>

<template>
  <NavBar :logo="logoSrc" :alt="appName" />
  <RouterView />
  <FooterComponent />
</template>

<style scoped lang="scss"></style>
