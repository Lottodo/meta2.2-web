<template>
  <v-table style="width: fit-content;">
    <thead>
      <tr>
        <th>Columna 1</th>
        <th>Columna 2</th>
        <th>Columna 3</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(fila, i) in valores" :key="i">
        <td v-for="(celda, j) in fila" :key="j">{{ celda }}</td>
      </tr>
    </tbody>
  </v-table>
</template>

<script setup lang="ts">
  const valores = [
    ['Valor 1', 'Valor 2', 'Valor 3'],
    ['Valor 4', 'Valor 5', 'Valor 6'],
    ['Valor 7', 'Valor 8', 'Valor 9'],
  ]
</script>
