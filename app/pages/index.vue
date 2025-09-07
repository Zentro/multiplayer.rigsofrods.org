<template>
  <section>
    <section
      class="bg-center bg-no-repeat bg-cover bg-[url('https://cdn.discordapp.com/attachments/406612300406063116/1406259144708587591/image.png?ex=68be28a3&is=68bcd723&hm=0d36f482e1bba4f063747eb7bac850fff51d8525a2f549ea027b132b0d1257aa')] bg-neutral-700 bg-blend-multiply">
      <div class="px-4 mx-auto max-w-screen-xl py-24 lg:py-32">
        <h1 class="mb-2 text-4xl font-extrabold tracking-tight leading-none text-white md:text-5xl lg:text-6xl">
          Multiplayer</h1>
      </div>
    </section>

    <div class="max-w-screen-xl px-4 py-8 mx-auto text-center lg:py-16 lg:px-6">
      <dl class="grid max-w-screen-md gap-8 mx-auto text-gray-900 sm:grid-cols-3 dark:text-white">
        <div class="flex flex-col items-center justify-center">
          <dt class="mb-2 text-3xl md:text-4xl font-extrabold">12</dt>
          <dd class="font-light text-gray-500 dark:text-gray-400">servers</dd>
        </div>
        <div class="flex flex-col items-center justify-center">
          <dt class="mb-2 text-3xl md:text-4xl font-extrabold">18</dt>
          <dd class="font-light text-gray-500 dark:text-gray-400">players currently playing</dd>
        </div>
        <div class="flex flex-col items-center justify-center">
          <dt class="mb-2 text-3xl md:text-4xl font-extrabold">4M+</dt>
          <dd class="font-light text-gray-500 dark:text-gray-400">races</dd>
        </div>
      </dl>
    </div>

    <div class="py-8 px-4 mx-auto max-w-screen-xl sm:py-16 lg:px-6">

      <!-- Search & Filter -->
      <div
        class="flex flex-col sm:flex-row sm:items-center sm:justify-between mb-4 space-y-2 sm:space-y-0 sm:space-x-2">
        <!-- Search input -->
        <input v-model="searchQuery" type="text" placeholder="Search for servers by name, IP, terrain..."
          class="flex-1 px-4 py-2 rounded border border-neutral-700 bg-neutral-800 text-neutral-100 placeholder-neutral-500 focus:outline-none focus:ring-2 focus:ring-blue-300">

        <!-- Filter button -->
        <button
          class="px-4 py-2 rounded bg-neutral-700 hover:bg-primary/50 text-white transition border border-neutral-700"
          @click="toggleFilter">
          {{ selectedFilter ? selectedFilter : "Filter by..." }}
        </button>
      </div>

      <!-- Scrollable server list -->
      <div class="h-[500px] overflow-y-auto bg-neutral-900 rounded">
        <a v-for="server in filteredServers" :key="server.id" href="#"
          class="flex items-center w-full border-b border-neutral-700 hover:bg-blue-300/50 transition-all px-4 py-3 cursor-pointer no-underline">
          <!-- Left: server icon + info -->
          <div class="flex items-center space-x-3 flex-1 min-w-0">
            <img class="w-10 h-10 rounded" :src="server.icon" alt="Server icon">
            <div class="min-w-0">
              <div class="text-base font-semibold text-neutral-100 truncate">
                {{ server.name }}
              </div>
              <div class="font-normal text-neutral-400 truncate hidden sm:block">
                {{ server.ip }}
              </div>
            </div>
          </div>

          <!-- Middle: player count -->
          <div class="text-sm text-neutral-100 w-20 text-right shrink-0 hidden md:block">
            {{ server.players }} / {{ server.maxPlayers }}
          </div>

          <!-- Right: region/lang -->
          <div class="text-sm text-neutral-100 w-60 text-right shrink-0 hidden md:block">
            {{ server.region }} {{ server.language }}
          </div>
        </a>

        <!-- Empty state -->
        <div v-if="filteredServers.length === 0" class="text-neutral-400 text-center py-4">
          No servers found.
        </div>
      </div>
    </div>

    <div class="max-w-screen-xl px-4 py-8 mx-auto text-center lg:py-16 lg:px-6">


      <div class="relative overflow-x-auto">
        <table class="w-full text-sm text-left rtl:text-right text-gray-500 dark:text-gray-400">
          <thead class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400">
            <tr>
              <th scope="col" class="px-6 py-3">
                Product name
              </th>
              <th scope="col" class="px-6 py-3">
                Color
              </th>
              <th scope="col" class="px-6 py-3">
                Category
              </th>
              <th scope="col" class="px-6 py-3">
                Price
              </th>
            </tr>
          </thead>
          <tbody>
            <tr class="bg-white border-b dark:bg-gray-800 dark:border-gray-700 border-gray-200">
              <th scope="row" class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-white">
                Apple MacBook Pro 17"
              </th>
              <td class="px-6 py-4">
                Silver
              </td>
              <td class="px-6 py-4">
                Laptop
              </td>
              <td class="px-6 py-4">
                $2999
              </td>
            </tr>
            <tr class="bg-white border-b dark:bg-gray-800 dark:border-gray-700 border-gray-200">
              <th scope="row" class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-white">
                Microsoft Surface Pro
              </th>
              <td class="px-6 py-4">
                White
              </td>
              <td class="px-6 py-4">
                Laptop PC
              </td>
              <td class="px-6 py-4">
                $1999
              </td>
            </tr>
            <tr class="bg-white dark:bg-gray-800">
              <th scope="row" class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-white">
                Magic Mouse 2
              </th>
              <td class="px-6 py-4">
                Black
              </td>
              <td class="px-6 py-4">
                Accessories
              </td>
              <td class="px-6 py-4">
                $99
              </td>
            </tr>
          </tbody>
        </table>
      </div>

      <div class="grid gap-6 sm:grid-cols-2 lg:grid-cols-3">
        <div class="max-w-sm bg-primary/50 shadow-lg rounded-md p-6">
          <h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900">Test</h5>
          <a href="#"
            class="inline-flex items-center px-4 py-2 text-sm font-medium text-white bg-blue-600 rounded-lg hover:bg-blue-700 focus:ring-4 focus:ring-blue-300 transition-colors">
            View Competitions
          </a>
        </div>
      </div>

    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue'

const searchQuery = ref('')
const selectedFilter = ref(null)

// Example servers
const servers = ref([
  {
    id: 1,
    name: "Really Cool Roleplay Server",
    ip: "play.mycoolserver.com:12000",
    players: 12,
    maxPlayers: 32,
    region: "🇺🇸",
    language: "American English",
    icon: "https://placehold.co/40x40",
    type: "Roleplay",
    terrain: "Urban"
  },
  {
    id: 2,
    name: "Another Fun Server",
    ip: "play.another.com:12000",
    players: 5,
    maxPlayers: 20,
    region: "🇬🇧",
    language: "British English",
    icon: "https://placehold.co/40x40",
    type: "PvP",
    terrain: "Desert"
  },
  {
    id: 3,
    name: "Chill Roleplay Server",
    ip: "play.chill.com:13000",
    players: 8,
    maxPlayers: 16,
    region: "🇺🇸",
    language: "American English",
    icon: "https://placehold.co/40x40",
    type: "Roleplay",
    terrain: "Forest"
  },
])
const filteredServers = computed(() => {
  const query = searchQuery.value.toLowerCase()

  return servers.value.filter(server => {
    // Search by multiple fields
    const matchesSearch =
      server.name.toLowerCase().includes(query) ||
      server.ip.toLowerCase().includes(query) ||
      (server.terrain && server.terrain.toLowerCase().includes(query))

    const matchesFilter = selectedFilter.value ? server.type === selectedFilter.value : true
    return matchesSearch && matchesFilter
  })
})


// Toggle filter button (example cycle through types)
const filterOptions = ["Roleplay", "PvP", "Survival"]
function toggleFilter() {
  if (!selectedFilter.value) {
    selectedFilter.value = filterOptions[0]
  } else {
    const currentIndex = filterOptions.indexOf(selectedFilter.value)
    selectedFilter.value = filterOptions[(currentIndex + 1) % filterOptions.length]
  }
}

definePageMeta({
  layout: 'default'
})
</script>
