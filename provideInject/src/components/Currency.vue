<script setup>
import { provide, ref } from 'vue';

const currencies = ref([
    {name: 'EUR', rate: 1}, // Euro
    {name: 'USD', rate: 1.1}, // Dòlar americà
    {name: 'GBP', rate: 0.85} // Lliura esterlina
]);

const selectedCurrency = ref(currencies.value[0]);

function updateCurrency(event) {
    const selected = currencies.value.find(currency => currency.name === event.target.value);
    if (selected) {
        selectedCurrency.value = selected;
    }
}

provide('selectedCurrency', selectedCurrency);
</script>

<template>
    <div>
        <label for="currency">Currency: </label>
        <select id="currency" @change="updateCurrency">
            <option v-for="currency in currencies" :key="currency.name" :value="currency.name">
                {{ currency.name }}
            </option>
        </select>
    </div>
</template>