<script setup>
// Importem 'ref' i 'provide' de Vue.
import { provide, ref, inject } from 'vue';

const currencies = ref([
    {name: 'EUR', rate: 1}, // Euro
    {name: 'USD', rate: 1.1}, // Dòlar americà
]);

const selectedCurrency = ref('EUR');
const exchangeCurrency = ref(1);

// Actualitza la divisa seleccionada quan canvia la selecció.
function updateCurrency(event) {
    const selected = currencies.value.find(currency => currency.name === event.target.value);
    if (selected) {
        selectedCurrency.value = selected;
    }
}

const updateCurrency = () => {
    exchangeCurrency.value = selectedCurrency.value === 'USD' ? 1.1 : 1;
}

provide('selectedCurrency', selectedCurrency);
</script>

<template>
    <div>
        <label for="currency">Currency: </label>
        <select id="currency" @change="updateCurrency">
            <!-- Passem 'currency.name' al valor per a la selecció -->
            <option v-for="currency in currencies" :key="currency.name" :value="currency.name">
                {{ currency.name }}
            </option>
        </select>
    </div>
</template>
