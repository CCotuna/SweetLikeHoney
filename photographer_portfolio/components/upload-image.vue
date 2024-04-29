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

async function uploadPicture() {
    const file = files.value?.[0]
    if (file) {
        try {
            const fileRef = storageRef(storage, `${folderPath}/${file.name}`)
            await uploadBytes(fileRef, file)
            console.log('File uploaded successfully!')
            showAlert.value = true
            setTimeout(() => {
                showAlert.value = false
            }, 1000)
        } catch (error) {
            console.error('Error uploading file:', error)
        }
    }
}
</script>

<template>
    <form @submit.prevent="uploadPicture">
        <fieldset>
            <button type="button" @click="open({ accept: 'image/*,video/*', multiple: false })">
                <template v-if="files?.length === 1">
                    Selected file: {{ files.item(0)?.name }} (Click to select another)
                </template>
                <template v-else>
                    Select an image or video
                </template>
            </button>

            <br />

            <button type="submit">Upload</button>
        </fieldset>

        <div v-if="showAlert" class="fixed top-4 right-4 bg-emerald-500 text-white px-4 py-2 rounded shadow-lg">
            File uploaded successfully!
        </div>
    </form>
</template>
