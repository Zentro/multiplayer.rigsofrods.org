<template>
    <div>
        <div class="mx-auto max-w-screen-xl sm:py-16 lg:px-6 mt-12">
            <div class="bg-neutral-900/50 rounded-lg shadow-lg shadow-neutral-900/50 p-6">
                <div class="grid grid-cols-1 md:grid-cols-3 gap-6 items-start">

                    <!-- Larger section -->
                    <div class="md:col-span-2 flex flex-col md:flex-row items-start gap-6">
                        <!-- Server Icon -->
                        <img src="https://placehold.co/80x80" alt="Server Icon" class="w-24 h-24 rounded" />

                        <!-- Server Info -->
                        <div class="flex flex-col">
                            <h1 class="text-3xl font-bold text-white mb-4">
                                Free Drift, by Soft-Body Drift Club
                            </h1>
                            <p class="text-neutral-400">
                                Free Drift is a unique multiplayer experience that allows players to engage in thrilling
                                drift races.
                            </p>
                        </div>
                    </div>

                    <!-- Smaller section (Buttons) -->
                    <div class="flex flex-col gap-4">
                        <a href="#"
                            class="inline-flex items-center justify-center px-8 py-3 text-lg font-bold text-white bg-primary/50 border border-primary rounded-md shadow-md shadow-primary/50 transition-transform duration-300 ease-in-out hover:-translate-y-1 hover:scale-105">
                            <Icon name="fa6-solid:right-to-bracket" class="mr-2" />
                            Connect
                        </a>
                        <a href="#"
                            class="inline-flex items-center justify-center px-8 py-3 text-lg font-bold text-white bg-red-400/50 border border-red-400 rounded-md shadow-md shadow-red-400/50 transition-transform duration-300 ease-in-out hover:-translate-y-1 hover:scale-105">
                            <Icon name="fa6-solid:triangle-exclamation" class="mr-2" />
                            Report
                        </a>
                    </div>

                </div>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
definePageMeta({
  layout: 'default'
})
</script>