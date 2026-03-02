<template>
  <v-app>
    <Header />
    <v-main>
      <Hero />

      <v-container>
        <v-row>
          <TarjetaConImagen
            :autor="tarjeta1.autor"
            descripcion="Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed feugiat blandit dui vel rutrum."
            :imagen="tarjeta1.imagen"
            titulo="Tarjeta 1"
            @imagen-cargada="imagenesListas++"
          />
          <TarjetaConImagen
            :autor="tarjeta2.autor"
            descripcion="Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed feugiat blandit dui vel rutrum."
            :imagen="tarjeta2.imagen"
            titulo="Tarjeta 2"
            @imagen-cargada="imagenesListas++"
          />
        </v-row>
      </v-container>

      <v-container class="d-flex justify-center">
        <v-col class="d-flex flex-column align-center">
          <Tabla class="mb-4" />
          <BotonPicAPI class="mb-4" :disabled="imagenesListas < 2" @resultado="onResultado" />
        </v-col>
      </v-container>

    </v-main>

    <Footer />
  </v-app>

</template>

<script lang="ts" setup>
  import { ref } from 'vue'
  import Footer from '@/components/Footer.vue'
  import Hero from '@/components/Hero.vue'
  import TarjetaConImagen from '@/components/TarjetaConImagen.vue'
  import BotonPicAPI from './components/BotonPicAPI.vue'
  import Header from './components/Header.vue'
  import Tabla from './components/Tabla.vue'

  const tarjeta1 = ref({ autor: 'Autor', imagen: 'https://picsum.photos/seed/ohui/400/300?random=1' })
  const tarjeta2 = ref({ autor: 'Autor', imagen: 'https://picsum.photos/seed/owui/400/300?random=2' })
  const imagenesListas = ref(2)

  function onResultado (data: any[]) {
    console.log(data)
    imagenesListas.value = 0
    tarjeta1.value = { autor: data[0].author, imagen: data[0].download_url }
    tarjeta2.value = { autor: data[1].author, imagen: data[1].download_url }
  }
</script>
