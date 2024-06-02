<script setup lang="ts">
import { RouterView } from 'vue-router'
import NavBar from '@/components/header/NavBar.vue'
import FooterComponent from '@/components/FooterComponent.vue'
</script>

<template>
  <NavBar />
  <RouterView />
  <FooterComponent />
</template>

<style scoped lang="scss"></style>
