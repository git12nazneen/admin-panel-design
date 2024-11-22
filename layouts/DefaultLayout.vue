<script setup lang="ts">
import { ref } from 'vue'
import { Button } from '@/components/ui/button'
import { 
  Sheet, 
  SheetContent, 
  SheetHeader, 
  SheetTitle, 
  SheetTrigger 
} from '@/components/ui/sheet'
import { Menu, X, Home, Users, Folder, Calendar, BarChart } from 'lucide-vue-next'

const isSidebarOpen = ref(false)
const menuItems = [
    { name: 'Dashboard', icon: Home, href: '/' },
    { name: 'Team', icon: Users, href: '/team' },
    { name: 'Projects', icon: Folder, href: '/projects' },
    { name: 'Calendar', icon: Calendar, href: '/calendar' },
    { name: 'Reports', icon: BarChart, href: '/reports' },
  ]
const toggleSidebar = () => {
  isSidebarOpen.value = !isSidebarOpen.value
}


</script>

<template>
  <div class="min-h-screen bg-background flex flex-col">
    <!-- Header -->
    <header class="sticky top-0 z-40 w-full border-b bg-background">
      <div class="container flex h-16 items-center space-x-4 sm:justify-between sm:space-x-0">
        <div class="flex gap-6 md:gap-10">
          <Button variant="ghost" size="icon" class="md:hidden" @click="toggleSidebar">
            <Menu class="h-6 w-6" />
            <span class="sr-only">Toggle Sidebar</span>
          </Button>
          <a href="/" class="flex items-center space-x-2">
            <span class="inline-block font-bold">Your App</span>
          </a>
        </div>
        <div class="flex flex-1 items-center justify-end space-x-4">
          <!-- Add header content here (e.g., search, user menu) -->
        </div>
      </div>
    </header>

    <div class="flex-1 flex">
      <!-- Sidebar for larger screens -->
      <aside class="hidden md:flex w-64 flex-col bg-background border-r">
        <nav class="flex-1 space-y-1 p-4">
          <a 
            v-for="item in menuItems" 
            :key="item.name" 
            :href="item.href"
            class="flex items-center p-2 text-sm font-medium rounded-md hover:bg-accent hover:text-accent-foreground"
          >
            <component :is="item.icon" class="h-5 w-5 mr-3" />
            {{ item.name }}
          </a>
        </nav>
      </aside>

      <!-- Mobile sidebar -->
      <Sheet v-model:open="isSidebarOpen">
   
        <SheetContent side="left" class="w-64 p-0">
          <SheetHeader class="p-4 border-b">
            <SheetTitle>Menu</SheetTitle>
          </SheetHeader>
          <nav class="flex-1 space-y-1 p-4">
            <a 
              v-for="item in menuItems" 
              :key="item.name" 
              :href="item.href"
              class="flex items-center p-2 text-sm font-medium rounded-md hover:bg-accent hover:text-accent-foreground"
              @click="isSidebarOpen = false"
            >
              <component :is="item.icon" class="h-5 w-5 mr-3" />
              {{ item.name }}
            </a>
          </nav>
        </SheetContent>
      </Sheet>

      <!-- Main content -->
      <main class="flex-1 overflow-y-auto p-6">
        <slot />
      </main>
    </div>
  </div>
</template>