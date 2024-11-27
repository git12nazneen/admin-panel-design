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
import { Pyramid } from 'lucide-vue-next';
import { defineProps } from 'vue';

// Accept `isSidebarCollapsed` as a prop
defineProps({
    isSidebarCollapsed: Boolean,
});
</script>

<template>
    <Select>
        <!-- Dynamically adjust styles based on `isSidebarCollapsed` -->
        <SelectTrigger style="width: 225px;" :class="[
            '!w-[225px] border bg-white z-50 flex items-center',
            isSidebarCollapsed ? '!gap-5' : '!gap-10'
        ]">
            <div :class="isSidebarCollapsed ? 'sm:pr-5' : 'sm:pr-10'">
                <Pyramid />
            </div>
            <!-- Adjust placeholder visibility -->
            <SelectValue :class="isSidebarCollapsed ? 'text-[10px] hidden' : 'text-[12px]'"
                placeholder="Acme Inc Enterprise" />
        </SelectTrigger>

        <SelectContent class="absolute bg-white shadow-lg rounded-md z-50">
            <SelectGroup>
                <SelectLabel>Teams</SelectLabel>
                <SelectItem value="acmeInc">Acme Inc</SelectItem>
                <SelectItem value="acmeCorp">Acme Corp</SelectItem>
                <SelectItem value="acmeIndustry">Acme Industry</SelectItem>
            </SelectGroup>
        </SelectContent>
    </Select>
</template>
