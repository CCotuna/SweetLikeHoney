<script setup></script>
<template>
    <div class="flex flex-col sm:flex-row">
        <div class="flex flex-col items-center text-center">
            <h1
                class="mb-4 text-4xl font-extrabold leading-none tracking-tight text-gray-900 md:text-5xl lg:text-6xl dark:text-white">
                Sweet Like Honey <br> Photography </h1>
            <p class="mb-6 text-lg font-normal text-gray-500 lg:text-xl sm:px-16 xl:px-48 dark:text-gray-400">
                Preserve Your Moments in Timeless Elegance. <br> Book Your Photography Session Today</p>
            <a href="#"
                class="inline-flex items-center justify-center px-5 py-3 text-base font-medium text-center text-white bg-emerald-700 rounded-lg hover:bg-emerald-800 focus:ring-4 focus:ring-emerald-300 dark:focus:ring-emerald-900">
                <span>Book a Session</span>
                <i class="bi bi-flower3 text-xl "></i>
            </a>

        </div>
        <div>
            <ClientOnly>
                <Vue3Lottie animationLink="https://lottie.host/59612146-ef1c-45f6-87a7-f940008c1899/SvQLhEeZbo.json"
                    :height="200" :width="200" />
            </ClientOnly>
        </div>
    </div>
</template>
<style scoped></style>