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
import {
    Select,
    SelectContent,
    SelectGroup,
    SelectItem,
    SelectLabel,
    SelectTrigger,
    SelectValue,
} from '@/components/ui/select'
import { Menu, X, Home, Users, Folder, Calendar, BarChart } from 'lucide-vue-next'

const isOpen = ref(false)

const toggleSidebar = () => {
    isOpen.value = !isOpen.value
}

const menuItems = [
    { name: 'Dashboard', icon: Home, href: '/' },
    { name: 'Team', icon: Users, href: '/team' },
    { name: 'Projects', icon: Folder, href: '/projects' },
    { name: 'Calendar', icon: Calendar, href: '/calendar' },
    { name: 'Reports', icon: BarChart, href: '/reports' },
]
</script>

<template>
    <Sheet v-model:open="isOpen">
        <SheetTrigger asChild>
            <Button variant="outline" size="icon" class="fixed top-4 left-4 z-40 md:hidden">
                <Menu class="h-6 w-6" />
                <span class="sr-only">Toggle Sidebar</span>
            </Button>
        </SheetTrigger>
        <SheetContent side="left" class="w-[300px] sm:w-[400px]">
            <SheetHeader>
                <SheetTitle>Menu</SheetTitle>
            </SheetHeader>
            <nav class="flex flex-col space-y-4 mt-4">
                <a v-for="item in menuItems" :key="item.name" :href="item.href"
                    class="flex items-center px-2 py-1 rounded-md hover:bg-accent hover:text-accent-foreground transition-colors"
                    @click="isOpen = false">
                    <component :is="item.icon" class="mr-2 h-4 w-4" />
                    {{ item.name }}
                </a>
            </nav>
        </SheetContent>
    </Sheet>

    <!-- Desktop Sidebar -->
    <div class="hidden md:flex flex-col w-64 bg-background h-screen border-r">
        <div class="p-4 border-b">
            <h2 class="text-2xl font-semibold">Your App</h2>
        </div>


        <nav class="flex flex-col space-y-2 p-4">
           
            <Select>
                <SelectTrigger class="w-[180px] border p-2 bg-gray-100">
                    <SelectValue placeholder="Select a fruit" />
                </SelectTrigger>
                <SelectContent class="absolute bg-white shadow-lg rounded-md z-50">
                    <SelectGroup>
                        <SelectLabel>Fruits</SelectLabel>
                        <SelectItem value="apple">Apple</SelectItem>
                        <SelectItem value="banana">Banana</SelectItem>
                        <SelectItem value="blueberry">Blueberry</SelectItem>
                        <SelectItem value="grapes">Grapes</SelectItem>
                        <SelectItem value="pineapple">Pineapple</SelectItem>
                    </SelectGroup>
                </SelectContent>
            </Select>
            <a v-for="item in menuItems" :key="item.name" :href="item.href"
                class="flex items-center px-2 py-1 rounded-md hover:bg-accent hover:text-accent-foreground transition-colors">
                <component :is="item.icon" class="mr-2 h-4 w-4" />
                {{ item.name }}
            </a>
        </nav>
    </div>
</template>