<script setup lang="ts">
import { Accordion, AccordionContent, AccordionItem, AccordionTrigger } from '@/components/ui/accordion'
import { BookCopy, BadgeCheck, AppWindowMac } from 'lucide-vue-next'

const defaultValue = 'item-1'
const accordionItems = [
  { value: 'item-1', title: 'Model', content: ['History', 'Details'], icon: BookCopy },
  { value: 'item-2', title: 'Playground', content: ['Examples', 'Starred'], icon: BadgeCheck },
  { value: 'item-3', title: 'Documentation', content: ['Overview', 'Guides'], icon: AppWindowMac },
]
</script>

<template>
  <Accordion type="single" class="w-full" collapsible :default-value="defaultValue">
    <AccordionItem v-for="item in accordionItems" :key="item.value" :value="item.value">
      <!-- Accordion Header with Trigger -->
      <AccordionTrigger class="font-medium text-[12px] flex items-center justify-start gap-2 p-2 hover:bg-gray-100 rounded-md">
        <!-- Render Icon -->
        <component :is="item.icon" class="w-5 h-5 text-gray-600" />
        <span class="pl-7">{{ item.title }}</span>
      </AccordionTrigger>
      
      <!-- Accordion Content -->
      <AccordionContent>
        <ul class="pl-8 space-y-2">
          <li
            v-for="(text, index) in item.content"
            :key="index"
            class="text-[12px] py-1 px-2 rounded-md hover:bg-gray-200 transition cursor-pointer"
          >
            {{ text }}
          </li>
        </ul>
      </AccordionContent>
    </AccordionItem>
  </Accordion>
</template>
