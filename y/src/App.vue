
<script setup>
import { ref } from 'vue'
import Header from './components/Header.vue'
import Todoformulier from './components/Todoformulier.vue'
import TodoLijst from './components/Todolijst.vue'

const taken = ref([])

function taakToevoegen(naam) {
  taken.value.push({
    id: Date.now(),
    naam: naam,
    voltooid: false,
    prioriteit: 'Middel'
  })
}

function taakVoltooien(id) {
  const taak = taken.value.find(taak => taak.id === id)

  if (taak) {
    taak.voltooid = !taak.voltooid
  }
}

function taakVerwijderen(id) {
  taken.value = taken.value.filter(taak => taak.id !== id)
}
</script>

<template>
  <div class="p-5 ">
    <Header />

    <Todoformulier @taak-toevoegen="taakToevoegen" />

    <TodoLijst
      :taken="taken"
      @taak-voltooien="taakVoltooien"
      @taak-verwijderen="taakVerwijderen"
    />
  </div>
</template>
