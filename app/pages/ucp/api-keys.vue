<template>
    <div>
        <div class="flex items-center justify-between">
            <h1 class="text-2xl font-bold">API Keys</h1>
            <button class="inline-flex items-center justify-center px-4 py-2 text-base font-bold text-white 
                bg-primary/50 border border-primary rounded-md shadow-md shadow-primary/50" @click="openCreate = true">
                <Icon name="fa6-solid:plus" class="mr-2" />
                Add API key
            </button>
        </div>

        <!-- Create Dialog -->
        <AppDialog :open="openCreate" title="Create API Key" confirmText="Create key" @close="openCreate = false"
            @confirm="createKey">
            <input v-model="form.name" placeholder="Key Name"
                class="w-full p-2 rounded border border-neutral-700 bg-neutral-800 text-neutral-100 placeholder-neutral-500 focus:outline-none focus:ring-2 focus:ring-blue-300" />
        </AppDialog>

    </div>
</template>

<script setup>
import AppDialog from '~/components/AppDialog.vue';

const keys = ref([
  { id: 1, name: 'Main Key' },
  { id: 2, name: 'Backup Key' },
])

const openCreate = ref(false)
// const openEditDialog = ref(false)
// const openDeleteDialog = ref(false)

const form = ref({ id: null, name: '' })

// Create
const createKey = () => {
  keys.value.push({ id: Date.now(), name: form.value.name })
  form.value.name = ''
  openCreate.value = false
}

// // Edit
// const openEdit = (key) => {
//   form.value = { ...key }
//   openEditDialog.value = true
// }
// const updateKey = () => {
//   const idx = keys.value.findIndex((k) => k.id === form.value.id)
//   if (idx > -1) keys.value[idx].name = form.value.name
//   openEditDialog.value = false
// }

// // Delete
// const openDelete = (key) => {
//   form.value = { ...key }
//   openDeleteDialog.value = true
// }
// const deleteKey = () => {
//   keys.value = keys.value.filter((k) => k.id !== form.value.id)
//   openDeleteDialog.value = false
// }

definePageMeta({
    layout: 'dashboard'
})
</script>