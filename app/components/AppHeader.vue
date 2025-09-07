<template>
    <Disclosure as="nav" class="bg-transparent absolute w-full z-10">
        <div class="max-w-screen-xl flex flex-wrap items-center justify-between mx-auto p-4">
            <a href="/" class="flex items-center space-x-3 rtl:space-x-reverse">
                <img src="~/assets/img/ror-logo.png" class="h-8" alt="Rigs of Rods Logo" />
            </a>
            <DisclosureButton data-collapse-toggle="navbar-solid-bg" type="button"
                class="inline-flex items-center p-2 w-10 h-10 justify-center text-sm text-neutral-500 rounded-lg md:hidden hover:bg-neutral-100 focus:outline-none focus:ring-2 focus:ring-neutral-200 dark:text-neutral-400 dark:hover:bg-neutral-700 dark:focus:ring-neutral-600"
                aria-controls="navbar-solid-bg" aria-expanded="false">
                <span class="sr-only">Open main menu</span>
                <svg class="w-5 h-5" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none"
                    viewBox="0 0 17 14">
                    <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                        d="M1 1h15M1 7h15M1 13h15" />
                </svg>
            </DisclosureButton>
            <div class="hidden w-full md:block md:w-auto" id="navbar-solid-bg">
                <ul
                    class="flex flex-col font-thin mt-4 rounded-lg bg-neutral-50 md:space-x-8 rtl:space-x-reverse md:flex-row md:mt-0 md:border-0 md:bg-transparent dark:bg-neutral-800 md:dark:bg-transparent dark:border-neutral-700">
                    <!-- <li>
                        <a href="/download"
                            class="block py-2 px-3 md:p-0 text-gray-900 rounded hover:bg-gray-100 md:hover:bg-transparent md:border-0 md:hover:text-blue-700 dark:text-neutral-300 md:dark:hover:text-white dark:hover:bg-gray-700 dark:hover:text-white md:dark:hover:bg-transparent transition-all">Download</a>
                    </li> -->
                    <li v-for="item in navigation" :key="item.name">
                        <a :href="item.href" :class="[
                            'block py-2 px-3 md:p-0 text-neutral-900 rounded hover:bg-neutral-100 md:hover:bg-transparent md:border-0 transition-all',
                            item.current ? 'md:hover:text-blue-700 dark:text-neutral-300 md:dark:hover:text-white dark:hover:bg-neutral-700 dark:hover:text-white md:dark:hover:bg-transparent' : ''
                        ]">
                            {{ item.name }}
                        </a>
                    </li>
                </ul>
            </div>
            <!-- Profile section -->
            <div class="hidden md:flex items-center space-x-3 rtl:space-x-reverse ml-6">
                <img src="https://cdn.rigsofrods.org/data/avatars/l/0/5.jpg?1757221916" alt="Profile"
                    class="w-8 h-8 rounded-full" />
                <span class="text-neutral-900 dark:text-neutral-300 font-medium">Hello, Zentro</span>
            </div>
        </div>
        <DisclosurePanel class="sm:hidden">
            <div class="space-y-1 bg-neutral-700">
                <DisclosureButton v-for="item in navigation" :key="item.name" as="a" :href="item.href"
                    :class="[item.current ? 'text-white' : 'text-neutral-300 hover:bg-neutral-700 hover:text-white', 'block px-3 py-2 text-base font-medium']"
                    :aria-current="item.current ? 'page' : undefined">{{ item.name }}</DisclosureButton>
            </div>
        </DisclosurePanel>
    </Disclosure>
</template>

<script setup>
import { DisclosureButton, DisclosurePanel, Disclosure } from '@headlessui/vue'
const navigation = []
</script>