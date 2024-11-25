<script setup lang="ts">
import { ref } from 'vue'
import { Button } from '@/components/ui/button'
import Accordions from '@/component/Accordions.vue'
import Selection from '@/component/Selection.vue'
import BredCrump from '@/component/BredCrump.vue'
import { Menu, Home, Users, Folder, PanelLeft } from 'lucide-vue-next'

const isSidebarCollapsed = ref(false)

const menuItems = [
  { name: 'Dashboard', icon: Home, href: '/' },
  { name: 'Team', icon: Users, href: '/team' },
  { name: 'Projects', icon: Folder, href: '/projects' },
]

const toggleSidebarCollapse = () => {
  isSidebarCollapsed.value = !isSidebarCollapsed.value
}
</script>

<template>
  <div class="flex min-h-screen bg-background">
    <!-- Sidebar -->
    <aside :class="[ 
      'flex flex-col h-screen bg-[#fafafa] border-r transition-all duration-300 overflow-hidden',
      isSidebarCollapsed ? 'w-16' : 'w-64'
    ]">
      <div class="flex items-center justify-between p-4 border-b">
        <!-- Selection -->
        <Selection 
          :class="[
            'transition-all duration-300',
            isSidebarCollapsed ? 'scale-90 opacity-0 hidden' : 'scale-100 opacity-100'
          ]" 
        />
      </div>
      
      <!-- Navigation -->
      <nav class="flex-1 space-y-1 p-4">
        <h1 
          :class="[
            'transition-all duration-300',
            isSidebarCollapsed ? 'opacity-0 hidden' : 'opacity-100'
          ]">
          Platform
        </h1>
        <Accordions 
          :class="[
            'transition-all duration-300',
            isSidebarCollapsed ? 'opacity-0 hidden' : 'opacity-100'
          ]"
        />
        <h1 
          :class="[
            'transition-all duration-300',
            isSidebarCollapsed ? 'opacity-0 hidden' : 'opacity-100'
          ]">
          Projects
        </h1>
        
        <!-- Menu Items -->
        <a 
          v-for="item in menuItems" 
          :key="item.name" 
          :href="item.href" 
          class="flex items-center p-2 text-sm font-medium rounded-md hover:bg-accent hover:text-accent-foreground">
          <component :is="item.icon" class="h-5 w-5" />
          <span 
            :class="[
              'ml-3 transition-all duration-300',
              isSidebarCollapsed ? 'opacity-0 hidden' : 'opacity-100'
            ]">
            {{ item.name }}
          </span>
        </a>
      </nav>
    </aside>

    <!-- Main Content -->
    <main class="flex-1 overflow-y-auto">
      <header class="sticky top-0 z-40 w-full bg-white">
        <div class="container flex h-[71px] items-center space-x-4">
          <Button variant="ghost" size="icon" @click="toggleSidebarCollapse">
            <PanelLeft class="h-6 w-6" />
            <span class="sr-only">Toggle Sidebar</span>
          </Button>
          <BredCrump />
        </div>
      </header>
      <div class="p-4">
        <slot />
      </div>
    </main>
  </div>
</template>

<style scoped>
header {
  position: sticky;
  top: 0;
  z-index: 40;
  background-color: white;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

aside {
  transition: all 0.3s ease-in-out;
}

a {
  transition: background-color 0.2s ease-in-out;
}
</style>
