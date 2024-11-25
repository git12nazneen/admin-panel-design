<!-- <script setup lang="ts">
import { Accordion, AccordionContent, AccordionItem, AccordionTrigger } from '@/components/ui/accordion'

const defaultValue = 'item-1'

const accordionItems = [
  { value: 'item-1', title: 'Model',  content: ['History', 'Details'] },
  { value: 'item-2', title: 'Playground', content: 'Starred' },
  { value: 'item-3', title: 'Documentation', content: 'History' },
]
</script>

<template>
  <Accordion type="single" class="w-full" collapsible :default-value="defaultValue">
    <AccordionItem v-for="item in accordionItems" :key="item.value" :value="item.value">
      <AccordionTrigger>{{ item.title }}</AccordionTrigger>
      <AccordionContent>
        {{ item.content }}
      </AccordionContent>
    </AccordionItem>
  </Accordion>
</template> -->
<script setup lang="ts">
import { Accordion, AccordionContent, AccordionItem, AccordionTrigger } from '@/components/ui/accordion'

const defaultValue = 'item-1'

const accordionItems = [
  { value: 'item-1', title: 'Model', content: ['History', 'Details'] },
  { value: 'item-2', title: 'Playground', content: ['Examples', 'Starred'] },
  { value: 'item-3', title: 'Documentation', content: ['Overview', 'Guides'] },
]
</script>

<template>
  <Accordion type="single" class="w-full" collapsible :default-value="defaultValue">
    <AccordionItem v-for="item in accordionItems" :key="item.value" :value="item.value">
      <AccordionTrigger class="font-medium text-xl">{{ item.title }}</AccordionTrigger>
      <AccordionContent>
        <ul class="space-y-2">
          <li
            v-for="(text, index) in item.content"
            :key="index"
            class="text-sm  p-2 rounded-md hover:bg-gray-200 transition"
          >
            {{ text }}
          </li>
        </ul>
      </AccordionContent>
    </AccordionItem>
  </Accordion>
</template>

