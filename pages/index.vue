<template>
    <h1 class="mt-10 text-2xl text-center font-bold">Liste de pokemons</h1>
    <div class="flex justify-center mt-5">
        <input v-model="search" class="w-60 block p-4 ps-10 text-sm border border-gray-300 rounded-lg bg-gray-50 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 text-white" placeholder="Rechercher un pokemon" />
    </div>
    <div class="mx-auto px-4 sm:px-6 lg:px-40 lg:py-10 z-40">
        <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-5 gap-4">    
            <PokemonCard v-for="pokemon in data" :key="pokemon.id" :pokemon="pokemon" />
        </div>
    </div>
</template>

<script setup>
const search = ref('');
const {data, refresh} = useFetch('https://pokebuildapi.fr/api/v1/pokemon/limit/100')
</script>