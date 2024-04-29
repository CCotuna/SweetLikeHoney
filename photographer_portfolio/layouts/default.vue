<template>
    <div class="container mx-auto px-4 sm:px-6 lg:px-8">
        <header class="flex justify-between items-center mt-5 sm:mt-8 lg:mt-10">
            <div class="flex items-center space-x-4 sm:space-x-6 lg:space-x-10">
                <NuxtLink to="/"
                    class="font-cinzel text-lg sm:text-xl lg:text-2xl font-bold p-2 hover:text-emerald-600">
                    SweetLikeHoney🏵️
                </NuxtLink>
            </div>
            <div>
                <Navbar />
            </div>
        </header>
        <div v-if="showMobileMenu" class="mt-4 space-y-2">
            <Navbar />
        </div>
        <main class="p-2 mt-6 sm:mt-8 lg:mt-10">
            <slot />
        </main>
    </div>
</template>

<script setup>
useHead({
    title: 'About',
    link: [
        {
            rel: 'preconnect',
            href: 'https://fonts.googleapis.com'
        },
        {
            rel: 'stylesheet',
            href: 'https://fonts.googleapis.com/css2?family=Cinzel:wght@400..900&display=swap'
        }
    ]
})

const showMobileMenu = ref(false);
</script>

<style>
body {
    font-family: 'Roboto';
}

.font-cinzel {
    font-family: 'Cinzel', serif;
}

body {
    @apply bg-white dark:bg-emerald-900 text-gray-700 dark:text-white
}
</style>