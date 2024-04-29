<script setup>
import { getStorage, ref as storageRef, listAll, getDownloadURL } from 'firebase/storage'

const props = defineProps({
    folderPath: {
        type: String,
        required: true
    }
})

const photoUrls = ref([])
const isLoading = ref(true)

onMounted(async () => {
    try {
        const storage = getStorage()
        const imagesRef = storageRef(storage, props.folderPath)
        const snapshot = await listAll(imagesRef)

        for (const item of snapshot.items) {
            const downloadUrl = await getDownloadURL(item)
            photoUrls.value.push(downloadUrl)
        }
        isLoading.value = false
    } catch (error) {
        console.error('Error retrieving photos:', error)
        isLoading.value = false
    }
})
</script>

<template>
    <div v-if="isLoading" class="flex justify-center items-center mt-10">
        <div class="border-4 border-emerald-300 border-t-emerald-500 rounded-full w-12 h-12 animate-spin"></div>
    </div>
    <div v-else class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4">
        <div v-for="photoUrl in photoUrls" :key="photoUrl">
            <img :src="photoUrl" class="w-full h-auto" alt="Photo" />
        </div>
    </div>
</template>
<style scoped>
@keyframes spin {
    from {
        transform: rotate(0deg);
    }

    to {
        transform: rotate(360deg);
    }
}

.animate-spin {
    animation: spin 1s linear infinite;
}
</style>