<script setup>
import { RouterLink, RouterView } from 'vue-router'
import Navbar from './components/Navbar.vue';
import "bootstrap/dist/css/bootstrap.min.css"
import "bootstrap"
</script>

<template>
  <header>
    <Navbar></Navbar>
  </header>

  <RouterView />


</template>

<style scoped>

</style>
