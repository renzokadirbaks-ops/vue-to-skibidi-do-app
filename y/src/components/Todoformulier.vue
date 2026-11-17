
<script setup>
import { ref } from 'vue'

const nieuweTaak = ref('')

const emit = defineEmits(['taak-toevoegen'])

function taakToevoegen() {
  if (nieuweTaak.value.trim() === '') {
    return
  }

  emit('taak-toevoegen', nieuweTaak.value)
  nieuweTaak.value = ''
}
</script>

<template>
  <form @submit.prevent="taakToevoegen" class="my-4">
    <input
      v-model="nieuweTaak"
      placeholder="Nieuwe taak"
      class="border p-2"
    />

    <button class="ml-2 bg-blue-500 p-2 text-white">
      Toevoegen
    </button>
  </form>
</template>
