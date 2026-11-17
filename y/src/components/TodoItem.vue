
<script setup>
const { taak } = defineProps({
  taak: Object
})

const emit = defineEmits(['taak-voltooien', 'taak-verwijderen'])
</script>

<template>
  <div class="flex items-center gap-3 my-2">
    <input
      type="checkbox"
      :checked="taak.voltooid"
      @change="emit('taak-voltooien', taak.id)"
    />

    <span :class="{ 'line-through': taak.voltooid }">
      {{ taak.naam }}
    </span>

    <button
      @click="emit('taak-verwijderen', taak.id)"
      class="text-red-600"
    >
      Verwijderen
    </button>
  </div>
</template>
