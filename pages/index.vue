<template>
    <div class="mx-auto px-4 sm:px-6 lg:px-40 lg:py-10 z-40">
        <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-5 gap-4">    
            <PokemonCard v-for="pokemon in data" :key="pokemon.id" :pokemon="pokemon" />
        </div>
    </div>
</template>

<script setup>
const {data, refresh} = useFetch('https://pokebuildapi.fr/api/v1/pokemon/limit/100')
</script>