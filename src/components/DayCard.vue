<script setup lang="ts">
import type { IWeekDay } from '@/modules/WeekDay';
import { ref } from 'vue';

const props = defineProps<{
  day: IWeekDay;
}>();

function estado() {
    if (!props.day.selected) {
        return '"shadow-5xs bg-lime-50 p-5 rounded-lg flex flex-col items-center justify-center transition-colors"';
    } else {
        return '"shadow-5xs bg-violet-400 p-5 rounded-lg flex flex-col items-center justify-center transition-colors"';
    }

    
} 

</script>

<template>
<div v-bind:class="estado()"> 
    <p>{{ props.day.name }}</p>
</div>


    
</template>