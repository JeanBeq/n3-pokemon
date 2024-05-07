<template>
    <div v-for="pokemon in team" v-bind:key="pokemon.id">
        {{ pokemon }}
    </div>
</template>

<script setup>
const team = useState('team')
</script>