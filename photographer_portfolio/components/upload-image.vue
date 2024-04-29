<script setup>
// See https://vueuse.org/core/useFileDialog
import { useFileDialog } from '@vueuse/core'
import { getStorage, ref as storageRef, uploadBytes } from 'firebase/storage'

const storage = getStorage()
const folderPath = 'imageUploadTest'
const showAlert = ref(false)

const {
    files,
    open,
    reset,
} = useFileDialog()

async function uploadPictures() {
    if (files.value?.length) {
        try {
            for (const file of files.value) {
                const fileRef = storageRef(storage, `${folderPath}/${file.name}`)
                await uploadBytes(fileRef, file)
            }
            console.log('Files uploaded successfully!')
            showAlert.value = true
            setTimeout(() => {
                showAlert.value = false
            }, 3000)
        } catch (error) {
            console.error('Error uploading files:', error)
        }
    }
}
</script>

<template>
    <form @submit.prevent="uploadPictures">
        <fieldset>
            <button type="button" @click="open({ accept: 'image/*,video/*', multiple: true })">
                <template v-if="files?.length === 1">
                    Selected file: {{ files.item(0)?.name }} (Click to select another)
                </template>
                <template v-else-if="files?.length > 1">
                    {{ files.length }} files selected (Click to select more)
                </template>
                <template v-else>
                    Select one or more images or videos
                </template>
            </button>

            <br />

            <button type="submit">Upload</button>
        </fieldset>

        <div v-if="showAlert" class="fixed top-4 right-4 bg-emerald-500 text-white px-4 py-2 rounded shadow-lg">
            Files uploaded successfully!
        </div>
    </form>
</template>

<style scoped>
.fixed {
    position: fixed;
    z-index: 100;
}
</style>
