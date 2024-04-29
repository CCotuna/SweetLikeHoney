<script setup>
import { useFileDialog } from '@vueuse/core'
import { ref as storageRef } from 'firebase/storage'
import { useFirebaseStorage, useStorageFileUrl } from 'vuefire'

const storage = useFirebaseStorage()
const mountainFileRef = storageRef(storage, 'images/free-photo-of-a-white-flower-on-a-tree-branch-in-the-sun.jpeg')
const { url, refresh } = useStorageFileUrl(mountainFileRef)
</script>
<template>
    <div>
        <img :src="url" alt="Mountain" />
        <button @click="refresh">Refresh</button>
    </div>
</template>
<style scoped></style>