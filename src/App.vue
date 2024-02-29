<script setup>
//Importando funcion
//para referencias reactivas
import {ref} from 'vue'
//creando una referencias reactiva de tipo
// string
const header = ref('App Lista de compras');
const shoppingIcon = ref('material-icons shopping-cart-icon');

</script>

<template>
<h1><i v-bind:class="shoppingIcon">local_mall</i> {{ header }}</h1> 
</template>

<style scoped>
.Shopping-cart-icon{
  font-size:2rem;
}
</style>
