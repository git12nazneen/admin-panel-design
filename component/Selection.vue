<script setup lang="ts">
import {
    Select,
    SelectContent,
    SelectGroup,
    SelectItem,
    SelectLabel,
    SelectTrigger,
    SelectValue,
} from '@/components/ui/select'
</script>

<template>
    <Select>
        <SelectTrigger class="w-full border p-2 bg-gray-100">
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
</template>