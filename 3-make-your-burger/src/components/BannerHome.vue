<script setup lang="ts"></script>

<template>
  <section id="main-banner">
    <h2>Make Your Burger</h2>
  </section>
</template>

<style scoped lang="scss">
#main-banner {
  background-image: url('/img/burger.jpg');
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
  height: 500px;
  display: flex;
  align-items: center;
  justify-content: flex-start;

  h2 {
    color: #fff;
    text-align: center;
    font-size: 3.75rem;
    background-color: #222;
    padding: 1.25rem 2.5rem;
  }
}
</style>
