
<script setup>
import TodoItem from './TodoItem.vue'

defineProps({
  taken: Array
})

const emit = defineEmits(['taak-voltooien', 'taak-verwijderen'])
</script>

<template>
  <div>
    <p v-if="taken.length === 0">
      Nog geen taken toegevoegd.
    </p>

    <TodoItem
      v-for="taak in taken"
      :key="taak.id"
      :taak="taak"
      @taak-voltooien="emit('taak-voltooien', $event)"
      @taak-verwijderen="emit('taak-verwijderen', $event)"
    />
  </div>
</template>
