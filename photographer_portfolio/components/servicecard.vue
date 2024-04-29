<script setup></script>
<template>
    <div class="min-w-64 md:min-w-80 p-6 bg-white border border-gray-200 rounded-lg shadow-custom-card">
        <div class="flex items-center justify-center">
            <!-- <i :class="'bi bi' + service.icon + ' text-3xl rotate-center'"></i> -->
            <i class="'bi bi-star-fill text-3xl rotate-center'"></i>
        </div>
        <NuxtLink to="/about" class="block text-center mt-4">
            <h5 class="custom-font-cinzel-regular mb-2 text-2xl font-bold tracking-tight text-gray-900 fade-in-fwd">
                new title
            </h5>
        </NuxtLink>
        <p class="custom-font-old-standard-regular mb-3 font-normal text-gray-700 dark:text-gray-400 text-center">
            new description
        </p>
        <div class="flex items-center justify-center mt-4">
            <NuxtLink to="/portfolio"
                class="inline-flex items-center px-3 py-2 text-sm font-medium text-center text-white bg-emerald-800 rounded-lg hover:bg-white focus:ring-4 focus:outline-none focus:ring-emerald-300 dark:bg-emerald-800 dark:hover:bg-emerald-800 dark:focus:ring-emerald-800">
                Portofoliu</NuxtLink>
        </div>
    </div>
</template>
<style scoped></style>