<script setup>
import {useFavoritosStore} from '@/store/favoritos';
import { storeToRefs} from "pinia";
import { RouterLink } from 'vue-router';

const useFavoritos = useFavoritosStore();

const {favoritos} = storeToRefs(useFavoritos)
const {remove} = useFavoritos;

</script>

<template>
    <h1>
      Favoritos  
    </h1>
    <p v-if="favoritos.length === 0">Sin Favoritos</p>
    <ul class="list-group">
        <li 
            class="list-group-item" 
            v-for="pokemon in favoritos" 
            :key="pokemon.id">
        <div>
            {{ pokemon.name }}
        </div>
        <div>
            <router-link class="btn btn-sm btn-primary me-2" :to="`/pokemons/${pokemon.name}`">Mas informacion</router-link>
            <button class="btn btn-sm btn-danger" @click="remove(pokemon.id)">Eliminar</button>
        </div>
        </li>
    </ul>
</template>