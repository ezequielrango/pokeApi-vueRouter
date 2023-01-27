<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>

<nav class="navbar bg-body-tertiary bg-dark">
  <div class="container">
    <RouterLink class="navbar-brand" to="/">
      <img src="@/assets/logo.svg" alt="Logo" width="30" height="24" class="d-inline-block align-text-top">
      PokeApi
    </RouterLink>
    <div>
      <router-link class="btn btn-outline-primary" to="/">Home</router-link>
      <router-link class="btn btn-outline-primary ms-2" to="/pokemons">Pokemons</router-link>
    </div>
  </div>
</nav>
<div class="container text-center">
  <RouterView />

</div>
</template>
