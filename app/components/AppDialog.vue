<template>
    <!-- Teleport ensures the modal is appended to <body> (avoids parent stacking-context issues) -->
    <Teleport to="body">
        <Dialog :open="open" @close="onClose" class="fixed z-50">
            <!-- Overlay: explicitly lower z so it's under the panel -->
            <div class="fixed inset-0 bg-black/30" aria-hidden="true" />

            <!-- Centering container (panel sits above overlay) -->
            <div class="fixed inset-0 z-50 flex items-center justify-center p-4">
                <!-- PANEL: use max-w and w-auto so it doesn't force full width -->
                <DialogPanel
                    class="relative max-w-2xl w-auto rounded-lg bg-neutral-800 p-6 shadow-xl border border-neutral-700">

                    <DialogTitle as="h3" class="text-lg font-bold font-white">{{ title }}</DialogTitle>

                    <DialogDescription v-if="description" class="text-sm text-gray-400 mt-4">
                        {{ description }}
                    </DialogDescription>

                    <div class="mb-6">
                        <slot />
                    </div>

                    <div class="flex flex-row gap-3 mt-4">
                        <button class="items-center justify-center px-4 py-2 text-base font-bold text-white 
                bg-primary/50 border border-primary rounded-md"
                            @click="$emit('confirm')">{{ confirmText }}</button>
                        <button class="items-center justify-center px-4 py-2 text-base font-bold text-white 
                bg-neutral-500/50 border border-neutral-500 rounded-md"
                            @click="onClose">Cancel</button>
                    </div>
                </DialogPanel>
            </div>
        </Dialog>
    </Teleport>
</template>


<script setup lang="ts">
import { Teleport } from 'vue'
import {
    Dialog,
    DialogPanel,
    DialogTitle,
    DialogDescription,
} from '@headlessui/vue'

defineProps<{
    open: boolean
    title: string
    description?: string
    confirmText?: string
}>()

const emit = defineEmits<{
    (e: 'close'): void
    (e: 'confirm'): void
}>()

const onClose = () => emit('close')
</script>