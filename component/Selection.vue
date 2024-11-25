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
        <SelectTrigger style="width: 225px;" class="!w-[225px] border  bg-white z-50">
          
            <SelectValue class="text-[12px]" placeholder="   Acme Inc Enterprise" />
        </SelectTrigger>

        <SelectContent class="absolute bg-white shadow-lg rounded-md z-50"> 
            <SelectGroup>
                <SelectLabel>Teams</SelectLabel>
                <SelectItem value="acmeInc">Acme inc</SelectItem>
                <SelectItem value="acmeCorp">Acme Corp</SelectItem>
                <SelectItem value="acmeIndustry">Acme Industry</SelectItem>
            </SelectGroup>
        </SelectContent>
    </Select>
</template>