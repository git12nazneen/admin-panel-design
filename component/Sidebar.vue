<template>
    <aside
      :class="`flex flex-col bg-gray-100 text-black min-h-screen overflow-hidden transition-all duration-200 ${
        is_expanded ? 'w-64' : 'w-16'
      }`"
    >
      <!-- Logo -->
      <div class="flex justify-center items-center p-4">
        <span class="text-2xl font-bold tracking-wide">
          <span v-if="is_expanded">MyApp</span>
          <span v-else>L</span>
        </span>
      </div>
  
      <!-- Menu Toggle -->
      <div class="flex justify-end items-center px-2 py-2 transition-all duration-200">
        <button
          @click="ToggleMenu"
          class="p-2 rounded-md hover:bg-gray-700 focus:outline-none transition-transform duration-200"
        >
          <span
            class="material-icons text-xl transition-transform duration-200 transform"
            :class="{ 'rotate-180': is_expanded }"
          >
            arrow_forward
          </span>
        </button>
      </div>
  
      <!-- Menu Header -->
      <h3
        class="text-gray-400 text-sm uppercase px-4 py-2 tracking-widest opacity-0 transition-opacity duration-300"
        :class="{ 'opacity-100': is_expanded }"
      >
        Menu
      </h3>
  
      <!-- Menu Links -->
      <nav class="space-y-1 px-2">
        <router-link
          v-for="(item, index) in menuItems"
          :key="index"
          :to="item.route"
          class="group flex items-center rounded-md px-4 py-2 transition duration-200 hover:bg-gray-700"
          active-class="bg-gray-700"
        >
          <span class="material-icons text-lg text-gray-400 group-hover:text-white">
            {{ item.icon }}
          </span>
          <span
            class="ml-4 text-gray-300 opacity-0 transition-opacity duration-300"
            :class="{ 'opacity-100': is_expanded }"
          >
            {{ item.name }}
          </span>
        </router-link>
      </nav>
  
      <!-- Flex Spacer -->
      <div class="flex-1"></div>
  
      <!-- Settings Link -->
      <div class="px-2">
        <router-link
          to="/settings"
          class="group flex items-center rounded-md px-4 py-2 transition duration-200 hover:bg-gray-700"
          active-class="bg-gray-700"
        >
          <span class="material-icons text-lg text-gray-400 group-hover:text-white">
            settings
          </span>
          <span
            class="ml-4 text-gray-300 opacity-0 transition-opacity duration-300"
            :class="{ 'opacity-100': is_expanded }"
          >
            Settings
          </span>
        </router-link>
      </div>
    </aside>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  
  // Manage the sidebar state locally
  const is_expanded = ref(false)
  
  const ToggleMenu = () => {
    is_expanded.value = !is_expanded.value
  }
  
  // Define menu items dynamically
  const menuItems = [
    { name: 'Home', route: '/', icon: 'home' },
    { name: 'About', route: '/about', icon: 'description' },
    { name: 'Team', route: '/team', icon: 'group' },
    { name: 'Contact', route: '/contact', icon: 'email' },
  ]
  </script>
  
