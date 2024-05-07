<template>
    <h1 class="mt-10 text-2xl text-center font-bold">Team de pokemons</h1>
    <div class="mx-auto px-4 sm:px-6 lg:px-40 lg:py-10 z-40">
        <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-5 gap-4">    
            <PokemonCard v-for="pokemon in team" :key="pokemon.id" :pokemon="pokemon" />
        </div>
    </div>
</template>

<script setup>
const team = useState('team')
</script>