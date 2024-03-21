<script setup>
//Importando funcion para crear referencias reactivas
import { ref } from 'vue'
//Creando una referencia de tipo string
const header = ref('App Lista de compras');
const shoppingIcon = ref('material-icons shopping-cart-icon');
//Creando un referencia reactiva para almacenar el valor de la lista
const items = ref([
{id: 0, label:'Leche',purchased:false, highPriority:true},
{id: 1, label:'Arroz',purchased:false,highPriority:true},
{id: 2, label:'Carne',purchased:true,highPriority:false},
{id: 3, label:'Pan',purchased:false,highPriority:false},
{id: 4, label:'Galletas',purchased:true,highPriority:true},
{id: 5, label:'Cafe',purchased:true,highPriority:false},
]);
const togglePurchased = (item) =>{
  item.purchased = !  item.purchased
};

const newItem = ref('');
const newItemHighPriority = ref (false)

//Metodos
const saveItems = () => {
  //Agrega un nuevo elemento a la lista proveniente de la caja de texto 
  items.value.push({ id: items.value.length, label: newItem.value})
  //Borramos el contenido de la caja de texto
  newItem.value = "";
};

const showForm = ref(false);
const doShow = (edit) => {
  showForm.value = edit;
  newItem.value = "";
} 
</script>

<template>
  <div class="header">
  <h1> 
    <i v-bind:class="shoppingIcon">local_mall</i> {{ header }}
  </h1>
  <button class="btn btn-primary" v-on:click="doShow(false)" v-if="showForm">Cancelar</button>
  <button class="btn btn-primary" v-else v-on:click="doShow(true)">Agregar Articulo</button>
</div>
  <form v-if="showForm" v-on:submit.prevent="saveItems" class="add-item form">
    
    <input v-model="newItem" type="text" placeholder="Agregar Articulo">
  
    
    <label><input type="checkbox" v-model="newItemHighPriority">Alta Prioridad</label>
    <button class="btn btn-primary">
    Agrear Articulo</button>
    </form>
 
  <ul>
       
    <li v-for="({id, label,purchased,highPriority},index) in items"
    @click="togglePurchased(items[index])"
    :class="{priority:highPriority,strikeout:purchased}"
     v-bind:key="id">
     💀{{ label }}
    </li>
  </ul>
 <p v-if="items.length === 0">🥀No hay elementos en la lista🥀</p> 
</template>

<style scoped>
.shopping-cart-icon {
  font-size: 2rem;
}
</style>