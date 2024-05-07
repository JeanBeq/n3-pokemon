<template>
    <div class="bg-white rounded-lg shadow-md p-4 sm:p-6">
        <NuxtLink :to="`/pokemon/${pokemon.id}`">
          <img :src="pokemon.image" :alt="pokemon.name" class="w-full h-auto sm:h-64 object-cover mb-4 sm:mb-6 rounded-lg" />
        </NuxtLink>
        <button @click="addToTeam" :disabled="team.length >= 6" :class="{'bg-gray-500 hover:bg-gray-500': team.length >= 6}" class="px-4 py-2 bg-indigo-600 text-white rounded-md hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-indigo-600 focus:ring-opacity-50"><Icon name="fluent:person-add-16-regular" color="white"/></button>
    </div>
</template>

<script setup>
    const props = defineProps(['pokemon'])
    const team = useState('team', () => [])

    function addToTeam() {
        if (team.value.length < 6) {
            team.value.push(props.pokemon);
        }
    }
</script>
