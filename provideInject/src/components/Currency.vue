<script setup>
// Importem 'ref' i 'provide' de Vue.
import { provide, ref, inject } from 'vue';

const selectedCurrency = ref('€');

provide('selectedCurrency', selectedCurrency);
</script>

<template>
    <div>
        <label for="currency">Currency: </label>
        <select v-model="selectedCurrency">
            <option value="€">EUR</option>
            <option value="$">USD</option>
        </select>
    </div>
</template>
