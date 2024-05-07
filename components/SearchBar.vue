<template>
    <div class="flex justify-center mt-5">
        <input v-model="search" @input="$emit('update:modelValue', search)" class="w-60 block p-4 ps-10 text-sm border border-gray-300 rounded-lg bg-gray-50 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 text-white" placeholder="Rechercher un pokemon" />
    </div>
</template>
  
<script>
    export default {
        props: ['modelValue'],
        emits: ['update:modelValue'],
        setup(props, { emit }) {
            const search = computed({
            get: () => props.modelValue,
            set: (value) => emit('update:modelValue', value)
            });

            return { search };
        }
    };
</script>
  