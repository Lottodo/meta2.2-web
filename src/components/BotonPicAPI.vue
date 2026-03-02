<template>
  <v-btn :disabled="loading || disabled" variant="outlined" @click="fetchData">
    Reload
  </v-btn>
</template>

<script setup lang="ts">
  import { ref } from 'vue'

  // eslint-disable-next-line @typescript-eslint/no-unused-vars
  const props = defineProps<{ disabled?: boolean }>()
  const emit = defineEmits<{ resultado: [data: object[]] }>()
  const loading = ref(false)

  async function fetchData () {
    loading.value = true
    const page = Math.floor(Math.random() * 35)
    const response = await fetch(`https://picsum.photos/v2/list?page=${page}`)
    const data = await response.json()
    const shuffled = data.toSorted(() => Math.random() - 0.5)
    const selected = shuffled.slice(0, 2)
    emit('resultado', selected)
    loading.value = false
  }
</script>
