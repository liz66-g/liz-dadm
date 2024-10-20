<script setup>
import { ref } from "vue";
//modelo 
const header = ref('App lista de Compras');
// ---Items---
const items = ref([
    {id:'0', label: '10 bolillos',purchased: true, priority: true}, 
    {id:'1', label: '1 lata de volt',purchased: true, priority: true}, 
    {id:'2', label: '1 bote de café',purchased: false, priority: false},
    {id:'3', label: '10 chetos',purchased: false, priority: false}
]);
//Item-Method
const saveItem = () => {
    //Agregamos otro item
    items.value.push({id: items.value.length + 1, label: newItem.value});
    //queda vacia la caja de texto
    newItem.value = '';
    
}

const newItem = ref(''); 
const newItemHighPriority = ref(false);
const editing = ref(false);
const activateEdition = (activate) =>{ 
    editing.value = activate;
};
//metodo para crear el hipervinculo
/*const hipervinculo = () => {
    return newItem.value === '' ? 'https://www.google.com' :
    'https://' + newItem.value;
}*/

</script>

<template>
<div class="header">
<h1>
    <i class="material-icons shopping-cart-icon">local_mall</i>
    {{ header }}
  </h1>
  <button v-if="editing" class="btn" @click="activateEdition(false)">CANCELAR</button>
  <button v-else class="btn btn-primary" @click="activateEdition(true)">AGREGAR ARTICULO</button>
</div>

<!-- Hipervinculo -->
<!--<a v-bind:href="hipervinculo()" target="_blank">
  {{ newItem == '' ? 'link' : newItem }}
</a>-->

<!-- Agrupando en un div las entradas -->
<form v-on:submit.prevent="saveItem()" v-if="editing" class="add-item fomr">

    <!-- entrada de texto -->
    <input
      v-model.trim="newItem"
      type="text"
      placeholder="Add Item">
    
    <!-- Caja de seleccion de prioridad -->
    <label>
      <input type="checkbox" v-model="newItemHighPriority" />
      Alta prioridad
    </label>
    <br>

    <!-- Boton -->
    <button class="btn btn-primary" 
    :disabled="newItem.length === 0"
    > Guardar </button>
  
</form>
    <!-- Lista de items objetos-->
    <ul>
    <li
         v-for="{label, id, purchased, priority} in items" 
         :key="id"
         class="amazing" 
         :class="{strikeout: purchased, priority: priority}"> 
         {{priority ? "🔥": "🛍️"}}
        {{label}} </li>
  </ul>
   
  <!-- Lista de items con arreglos-->
  <ul>
    <li
         v-for="{label, id, purchased, priority} in items" 
         :key="id"
         
         :class="[purchased ? 'strikeout' : '', priority ? 'priority' : '']"> 
         {{priority ? "🔥": "✨"}}
        {{label}} </li>
  </ul>
  <p v-if="items.length === 0"> 🥀NO HAY ELEMENTOS EN TU LISTA 🥀</p>
</template>

<style scoped>
.shopping-cart-icon{
    font-size: 2rem;
}
</style>