<!-- eslint-disable vue/custom-event-name-casing -->
<template>
  <v-card class="mx-auto" max-width="250">
    <v-img cover height="200" :src="imagen" @load="$emit('imagenCargada')" />
    <v-card-subtitle>
      {{ autor }}
    </v-card-subtitle>
    <v-card-title>
      {{ titulo }}
    </v-card-title>
    <v-card-text>{{ descripcion }}</v-card-text>
  </v-card>
</template>

<script>
  export default {
    name: 'TarjetaConImagen',
    props: {
      imagen: {
        type: String,
        required: true,
      },
      titulo: {
        type: String,
        required: true,
      },
      autor: {
        type: String,
        required: true,
      },
      descripcion: {
        type: String,
        required: true,
      },
    },
    emits: ['imagenCargada'],
  }
</script>

<style scoped>
  .round-3 {
      border-radius: 0.5rem;
  }
</style>
