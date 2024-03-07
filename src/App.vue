<script setup>
//Importando funcion
//para referencias reactivas
import { ref } from 'vue'
//creando una referencias reactiva de tipo
// string
const header = ref('App Lista de compras');
const shoppingIcon = ref('material-icons shopping-cart-icon');
//creando una referencia recreativa
//para almacenar el valor de la lista
const items= ref([
{id: 0, label:'leche'},
{id: 1, label:'Arroz'},
{id: 2, label:'Carne'},
{id: 3, label:'Pan'},
{id: 4, label:'Huevos'}
]);
const newItem = ref('');
const newItemHighPriority = ref(false) 
</script>

<template>
<h1><i v-bind:class="shoppingIcon">local_mall</i> {{ header }}</h1>
<input v-model="newItem" type="text" placeholder="Agregar articulo">
{{ newItem }}

<label><input type ="checkbox"v-model="newItemHighPriority">Alta Prioridad</label>
<ul>
  <li v-for="({id, label}, i) in items" v-bind:key="id">💀{{ label }}</li>
</ul> 
</template>

<style scoped>
.shopping-cart-icon {
  font-size: 2rem;
}
</style>