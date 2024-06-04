<script setup lang="ts">
import { RouterLink } from 'vue-router'

const { logo, alt } = defineProps<{ logo: string; alt: string }>()
</script>

<template>
  <header>
    <nav id="nav">
      <RouterLink to="/">
        <img :src="logo" :alt="alt" id="logo" />
      </RouterLink>
      <div class="navbar-links">
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/pedidos">Pedidos</RouterLink>
      </div>
    </nav>
  </header>
</template>

<style scoped lang="scss">
#nav {
  background-color: var(--color-black-soft);
  border-bottom: 4px solid #111;
  padding: 1rem 3rem;
  display: flex;
  justify-content: space-between;
  align-items: center;

  #logo {
    width: 40px;
    height: 40px;
  }

  a {
    margin: 0.75rem;
    transition: 0.5s;

    &:hover {
      color: #fff;
    }
  }
}
</style>
