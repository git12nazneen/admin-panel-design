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
      <AccordionTrigger class="font-medium text-[12px] flex items-center justify-start gap-2">
        <!-- Render Icon -->
        <component :is="item.icon" class="w-4 h-4 text-gray-600" />
        <span>{{ item.title }}</span>
      </AccordionTrigger>
      <AccordionContent>
        <ul class="space-y-2">
          <li
            v-for="(text, index) in item.content"
            :key="index"
            class="text-[12px] py-2  rounded-md hover:bg-gray-200 transition"
          >
            {{ text }}
          </li>
        </ul>
      </AccordionContent>
    </AccordionItem>
  </Accordion>
</template>
