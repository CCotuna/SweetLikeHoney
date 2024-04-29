<template>
    <div class="flex flex-col items-center">
        <Herosection />
        <div
            class="mt-10 p-5 md:p-0 grid grid-cols-1 sm:grid-cols-2 md:grid-cols-2 xl:grid-cols-3 2xl:grid-cols-4 gap-3 items-start ">
            <Servicecard v-for="i in 4" />
        </div>
    </div>
</template>
<script setup></script>
<style scoped></style>