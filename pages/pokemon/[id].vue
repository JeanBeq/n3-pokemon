<template>
    <h1 class="mt-10 text-2xl text-center font-bold">Pokemon {{ pokemon.name }}</h1>
    <div class="max-w-lg mx-auto bg-white rounded-lg shadow-md overflow-hidden">
      <img :src="pokemon.image" :alt="pokemon.name" class="w-full h-auto" />
      <div class="p-6">
        <h2 class="text-2xl font-bold mb-2">{{ pokemon.name }}</h2>
        <div class="flex items-center mb-4">
          <span class="text-gray-700 mr-2">ID:</span>
          <span>{{ pokemon.pokedexId }}</span>
        </div>
        <button v-if="!isInTeam(pokemon.id)" @click="addToTeam" :disabled="team.length >= 6" :class="{'bg-gray-500 hover:bg-gray-500': team.length >= 6}" class="px-4 py-2 bg-indigo-600 text-white rounded-md hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-indigo-600 focus:ring-opacity-50"><Icon name="fluent:person-add-16-regular" color="white"/></button>
      <button v-else @click="removeFromTeam(pokemon.id)" class="px-4 py-2 bg-red-600 text-white rounded-md hover:bg-red-700 focus:outline-none focus:ring-2 focus:ring-red-600 focus:ring-opacity-50"><Icon name="fluent:person-delete-24-regular" color="white"/></button>
        <div class="mb-4">
          <h3 class="text-lg font-semibold mb-2">Types:</h3>
          <div class="flex space-x-2">
            <div v-for="type in pokemon.apiTypes" :key="type.name" class="flex items-center">
              <img :src="type.image" :alt="type.name" class="w-6 h-6 mr-1" />
              <span>{{ type.name }}</span>
            </div>
          </div>
        </div>
        <div class="mb-4">
          <h3 class="text-lg font-semibold mb-2">Stats:</h3>
          <div class="grid grid-cols-2 gap-x-4 gap-y-2">
            <div v-for="(value, stat) in pokemon.stats" :key="stat" class="flex items-center">
              <span class="text-gray-700 mr-1">{{ stat }}:</span>
              <span>{{ value }}</span>
            </div>
          </div>
        </div>
        <div>
          <h3 class="text-lg font-semibold mb-2">Evolutions:</h3>
          <div v-if="pokemon.apiEvolutions.length" class="flex space-x-4">
            <div v-for="evolution in pokemon.apiEvolutions" :key="evolution.name" class="flex items-center">
              <span>{{ evolution.name }}</span>
              <span class="text-gray-500">(ID: {{ evolution.pokedexId }})</span>
            </div>
          </div>
          <span v-else class="text-gray-500">Pas d'évolution connue</span>
        </div>
      </div>
    </div>
  </template>

<script setup>
    const route = useRoute()
    const id = route.params.id
    const { data: pokemon } = await useFetch(`https://pokebuildapi.fr/api/v1/pokemon/${id}`)

    const props = defineProps(['pokemon'])
    const team = useState('team', () => [])
  
    function addToTeam() {
      if (team.value.length < 6 && !isInTeam(pokemon.id)) {
        team.value.push(props.pokemon);
      }
    }
  
    function removeFromTeam(id) {
      const index = team.value.findIndex(pokemon => pokemon.id === id);
      if (index !== -1) {
        team.value.splice(index, 1);
      }
    }
  
    function isInTeam(id) {
      return team.value.find(pokemon => pokemon.id === id) !== undefined;
    }
</script>
