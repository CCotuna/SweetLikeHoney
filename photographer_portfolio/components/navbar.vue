<template>
    <nav class="px-4 sm:px-6 lg:px-8">
        <div class="flex space-x-4 sm:space-x-6 lg:space-x-10 font-cinzel">
            <div class="hidden sm:block">
                <NuxtLink to="/" class="link">Homepage</NuxtLink>
            </div>
            <div class="hidden sm:block">
                <NuxtLink to="/about" class="link">About</NuxtLink>
            </div>
            <div class="hidden sm:block">
                <NuxtLink to="/portfolio" class="link">Portfolio</NuxtLink>
            </div>
            <div class="hidden sm:block">
                <NuxtLink to="/blog" class="link">Blogs</NuxtLink>
            </div>
            <div class="sm:hidden">
                <button @click="showMobileMenu = !showMobileMenu" class="focus:outline-none">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24"
                        stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                            d="M4 6h16M4 12h16M4 18h16" />
                    </svg>
                </button>
            </div>
        </div>
        <div v-if="showMobileMenu"
            class="absolute right-0 mt-4 bg-white dark:bg-gray-900 shadow-lg rounded-md p-4 space-y-2 z-10">
            <NuxtLink to="/" class="link block" @click="closeMobileMenu">Homepage</NuxtLink>
            <NuxtLink to="/about" class="link block" @click="closeMobileMenu">About</NuxtLink>
            <NuxtLink to="/portfolio" class="link block" @click="closeMobileMenu">Portfolio</NuxtLink>
            <NuxtLink to="/blog" class="link block" @click="closeMobileMenu">Blogs</NuxtLink>
        </div>
    </nav>
</template>

<script setup>
const showMobileMenu = ref(false);

function closeMobileMenu() {
    showMobileMenu.value = false;
}
</script>

<style scoped>
.link {
    @apply p-1 hover:bg-gray-200;
}
</style>