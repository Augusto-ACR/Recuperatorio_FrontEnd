<script setup lang="ts">
import type { IWeekDay } from '@/modules/WeekDay'
import { ref } from 'vue'
import DayCard from './DayCard.vue'

const days = ref<IWeekDay[]>([
  { id: 1, name: 'Lunes', selected: false },
  { id: 2, name: 'Martes', selected: false },
  { id: 3, name: 'Mièrcoles', selected: false },
  { id: 4, name: 'jueves', selected: false },
  { id: 5, name: 'viernes', selected: false },
  { id: 6, name: 'sabado', selected: false },
  { id: 7, name: 'domingo', selected: false },
])

function cambiarSeleccionados(id: number) {
  for (let index = 0; index < days.value.length; index++) {
    if (days.value[index]!.id === id) {
      days.value[index]!.selected = !days.value[index]!.selected
    } else {
      days.value[index]!.selected = false
    }
  }
}
</script>

<template>
  <div
    class="items-center gap-4 rounded-xl bg-white p-6 shadow-lg outline outline-black/5 justify-center m-4"
  >
    <h1>Gestor de dias de la semana</h1>
    <br />
    <h2>Elija un dia de la semana</h2>
    <br />
    <button
      v-for="day in days"
      :key="day.id"
      class="m-2 p-2 bg-violet-500 text-white rounded hover:bg-violet-700"
      @click="cambiarSeleccionados(day.id)"
    >
      {{ day.name }}
    </button>
  </div>

  <div class="flex flex-row items-center gap-4 rounded-xl bg-white p-6 shadow-lg outline outline-black/5 justify-center m-4">
    <DayCard v-for="day in days" :key="day.id" :day="day" />
  </div>
</template>
