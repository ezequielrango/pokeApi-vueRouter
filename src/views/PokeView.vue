<script setup>
import { useRoute, useRouter } from 'vue-router';
import {useGetData} from '@/composables/getData' 
//para acceder al params
const route = useRoute();
const router = useRouter();


const {data , getData, error, loading} = useGetData();

const back = () => {
    router.push('/pokemons')
}

getData(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`);

</script>

<template>
    <p v-if="loading">Cargando información...</p>
    <div class="alert alert-danger mt-2" v-if="error">
        {{ error }}
    </div>
    <div v-if="data">
        <h1>Poke Name:{{ $route.params.name }}</h1>
        <img :src="data.sprites?.front_default" alt="">
    </div>
    <h1 v-else>No existe el pokemon</h1>
    <button @click="back()" class="btn btn-outline-primary">Back</button>
</template>