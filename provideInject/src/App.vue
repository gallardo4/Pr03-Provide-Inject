<script setup>
// Importem les funcions 'ref' i 'provide' de Vue per gestionar variables reactives i compartir dades amb altres components.
import { ref } from 'vue';
// Importem el component 'Products' des de la carpeta 'components'.
import Products from './components/Products.vue';

// Definim una variable reactiva 'orderName' per emmagatzemar el nom de la comanda.
const orderName = ref('');
</script>

<template>
  <div>
    <!-- Mostrem el nom de la comanda i un input per canviar-lo dinàmicament amb v-model -->
    <h1>{{ orderName }}</h1>
    <input v-model="orderName" placeholder="Order name" />

    <!-- Incloem el component 'Products' per mostrar i gestionar els productes -->
    <Products />
  </div>
</template>