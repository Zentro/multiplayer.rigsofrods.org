<template>
    <div class="min-h-screen bg-neutral-800 flex flex-col">
        <!-- Navbar -->
        <nav class="fixed top-0 left-0 z-50 w-full bg-neutral-900 border-b border-neutral-800">
            <div class="flex items-center justify-between p-4">
                <!-- Mobile menu button -->
                <button data-drawer-target="default-sidebar" data-drawer-toggle="default-sidebar"
                    aria-controls="default-sidebar" type="button"
                    class="inline-flex items-center p-2 text-neutral-300 rounded-lg sm:hidden hover:bg-neutral-800 focus:outline-none focus:ring-2 focus:ring-neutral-700">
                    <span class="sr-only">Open sidebar</span>
                    <svg class="w-6 h-6" aria-hidden="true" fill="currentColor" viewBox="0 0 20 20">
                        <path clip-rule="evenodd" fill-rule="evenodd" d="M2 4.75A.75.75 0 012.75 4h14.5a.75.75 0 010 
             1.5H2.75A.75.75 0 012 4.75zm0 
             10.5a.75.75 0 01.75-.75h7.5a.75.75 
             0 010 1.5h-7.5a.75.75 
             0 01-.75-.75zM2 10a.75.75 
             0 01.75-.75h14.5a.75.75 
             0 010 1.5H2.75A.75.75 
             0 012 10z"></path>
                    </svg>
                </button>
                <img src="~/assets/img/ror-logo.png" class="h-8" alt="Rigs of Rods Logo" />
                <h1 class="text-white font-bold">User Control Panel</h1>
            </div>
        </nav>

        <!-- Sidebar -->
        <aside id="default-sidebar"
            class="fixed top-0 left-0 z-40 w-64 h-screen pt-16 transition-transform -translate-x-full sm:translate-x-0 bg-neutral-900 border-r border-neutral-800"
            aria-label="Sidenav">

            <div class="overflow-y-auto py-5 px-3 h-full">
                <ul class="space-y-2">
                    <li>
                        <a href="#"
                            class="flex items-center p-2 text-base font-semibold text-neutral-200 rounded-lg hover:bg-neutral-800 group">
                            <Icon name="fa6-solid:key" class="w-6 h-6 text-neutral-400 transition duration-75 group-hover:text-neutral-200" />
                            <span class="ml-3">API Keys</span>
                        </a>
                    </li>
                    <!-- Add more nav items here -->
                </ul>
            </div>
        </aside>

        <!-- Page content -->
        <div class="p-4 sm:ml-64 mt-16">
            <div class="p-4 rounded-lg bg-neutral-800 text-neutral-200">
                <slot />
            </div>
        </div>
    </div>
</template>