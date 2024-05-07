<template>
    <h1 class="mt-10 text-2xl text-center font-bold">Liste de pokemons</h1>
    <SearchBar v-model="search" />
    <p>{{ typesData }}</p>
    <div class="mx-auto px-4 sm:px-6 lg:px-40 lg:py-10 z-40">
        <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-5 gap-4">
            <PokemonCard v-for="pokemon in filteredPokemons" :key="pokemon.id" :pokemon="pokemon" />
        </div>
    </div>
</template>


<script setup>
import { ref, computed } from 'vue';

const search = ref('');
const {data, refresh} = useFetch('https://pokebuildapi.fr/api/v1/pokemon/limit/100')
const {typesData} = useFetch('https://pokebuildapi.fr/api/v1/type')

const filteredPokemons = computed(() => {
  return data.value.filter(pokemon => {
    return pokemon.name.toLowerCase().includes(search.value.toLowerCase());
  });
});
</script>
