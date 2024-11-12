<script setup>
// Importem 'ref', 'provide' i 'inject' de Vue.
import { ref, provide, inject } from 'vue';

// Importem el component 'Cart'.
import Cart from './Cart.vue';

// Importem el component 'Currency'.
import Currency from './Currency.vue';

// Definim un array de productes amb els seus noms i preus.
const products = ref([
  { name: "Hamburger 🍔", price: 5 },
  { name: "Cheeseburger 🧀", price: 6 },
  { name: "Impossible Burger 🥕", price: 7 },
  { name: "Fries 🍟", price: 2 }
]);

const selectedCurrency = inject('selectedCurrency');

function getConvertedPrice(price) {
    if (selectedCurrency == '€') return price;
    return (price * 1.1);
}

// Definim una variable reactiva 'cart' que emmagatzema els productes afegits a la cistella.
const cart = inject('cart');

// Funció per afegir un producte a la cistella. Mostrem un 'alert' per confirmar que s'ha afegit.
function addToCart(product) {
    cart.value.push(product);

    const cartItems = cart.value.map(item => item.name).join(', ');    

    alert(`Your cart: ${cartItems}`);
}
</script>

<template>
    <Currency />

    <!-- Iterem sobre l'array de productes per mostrar el nom i el preu de cada producte, amb un botó per afegir a la cistella -->
    <div v-for="product in products" :key="product.name">
        <p>{{ product.name }} - {{ getConvertedPrice(product.price.toFixed(2)) }} {{ selectedCurrency }}</p>
        <button @click="addToCart(product)">Add to the cart</button>
    </div>

    <!-- Incloem el component 'Cart' per mostrar els productes afegits a la cistella -->
    <Cart />
</template>