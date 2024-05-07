<template>
    <div class="flex justify-center z-50">
        <div class="fixed bottom-10 w-full max-w-screen-xl mx-auto px-4 flex items-center justify-around">
            <div class="bg-gray-800 flex items-center justify-around p-2 rounded-full shadow-lg text-white">
                <NuxtLink to="/" class="px-1 hover:text-white cursor-pointer flex items-center">
                    <Icon name="material-symbols-light:menu-book-outline" color="white" size="2em"/>
                    <span class="hidden md:block ml-2">Liste</span>
                </NuxtLink>
                <NuxtLink to='/team' class="px-1 hover:text-white cursor-pointer flex items-center">
                    <Icon name="fluent:people-team-48-filled" color="white" size="2em"/>
                    <span class="hidden md:block ml-2">Team</span>
                </NuxtLink>
            </div>
        </div>
    </div>
</template>

<script setup>

</script>