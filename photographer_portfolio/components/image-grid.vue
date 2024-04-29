<script setup>
import { getStorage, ref as storageRef, listAll, getDownloadURL } from 'firebase/storage'

const props = defineProps({
    folderPath: {
        type: String,
        required: true
    }
})

const photoUrls = ref([])

onMounted(async () => {
    try {
        const storage = getStorage()
        const imagesRef = storageRef(storage, props.folderPath)
        const snapshot = await listAll(imagesRef)

        for (const item of snapshot.items) {
            const downloadUrl = await getDownloadURL(item)
            photoUrls.value.push(downloadUrl)
        }
    } catch (error) {
        console.error('Error retrieving photos:', error)
    }
})
</script>

<template>
    <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4">
        <div v-for="photoUrl in photoUrls" :key="photoUrl">
            <img :src="photoUrl" class="w-full h-auto" alt="Photo" />
        </div>
    </div>
</template>
<style scoped></style>