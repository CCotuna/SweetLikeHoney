<template>
    <nav class="px-4 sm:px-6 lg:px-8">
        <div class="flex space-x-4 sm:space-x-6 lg:space-x-10 font-cinzel text-base">
            <div class="hidden sm:block hover:text-emerald-600">
                <NuxtLink to="/" class="link">Homepage</NuxtLink>
            </div>
            <div class="hidden sm:block hover:text-emerald-600">
                <NuxtLink to="/about" class="link">About</NuxtLink>
            </div>
            <div class="hidden sm:block hover:text-emerald-600">
                <NuxtLink to="/portfolio" class="link">Portfolio</NuxtLink>
            </div>
            <div class="hidden sm:block hover:text-emerald-600">
                <NuxtLink to="/blog" class="link">Blogs</NuxtLink>
            </div>
            <div class="sm:hidden">
                <button @click="showMobileMenu = !showMobileMenu" class="focus:outline-none">
                    <i class="bi bi-list text-2xl"></i>
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