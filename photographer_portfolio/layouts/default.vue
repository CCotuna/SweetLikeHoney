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
            href: 'https://fonts.googleapis.com/css2?family=Roboto&display=swap',
            crossorigin: ''
        }
    ]
})
</script>

<template>
    <div class="container mx-auto max-w-2xl">
        <header class="flex justify-between items-center mt-5">
            <div class="flex items-center space-x-10">
                <NuxtLink to="/" class="text-xl font-semibold p-2 hover:bg-gray-200">Homepage</NuxtLink>
                <NuxtLink to="/about" class="text-xl font-semibold p-2 hover:bg-gray-200">About</NuxtLink>
            </div>
        </header>
        <main class="p-2 mt-10">
            <slot />
        </main>
    </div>
</template>

<style>
body {
    font-family: 'Roboto';
}

body {
    @apply bg-white dark:bg-gray-900 text-gray-700 dark:text-gray-300
}
</style>