<script setup>

import {RouterLink} from 'vue-router';
import {useGetData} from '@/composables/getData'

const {data, loading,error, getData} = useGetData()

getData('https://pokeapi.co/api/v2/pokemon/');


</script>

<template>
    <h1>Pokemons</h1>
    <p v-if="loading">Cargando info</p>
    <div class="alert alert-danger mt-2" v-if="error">
        {{ error }}
    </div>
    <div v-if="data">
        <ul class="list-group">
            <li class="list-group-item" v-for="pokemon in data.results">
               <RouterLink :to="`/pokemons/${pokemon.name}`">{{ 
                pokemon.name 
                }}</RouterLink>
            </li>
            
        </ul>
        <div class="mt-2">
            <button :disabled="!data.previous" class="btn btn-warning me-2" @click="getData(data.previous)"> Previous</button>
            <button :disabled="!data.next" class="btn btn-success me-2" @click="getData(data.next)"> Next</button>
        </div>

    </div>
</template>