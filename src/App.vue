<script setup>
import { ref, computed } from 'vue';
// Modelo
const header = ref('App lista de compras');
//---items---
//Item-Model
const items = ref([
  {id:'0', label: '10 bolillos', purchased: false, priority: true},
  {id:'1', label: '1 crema de litro', purchased: true, priority: true},
  {id:'2', label: '1/4 de jamon', purchased: false, priority: false},
  {id:'3', label: '1 nutella', purchased: false, priority: true}
]);

//Item-Method
const saveItem = () => { 
  // Add new item
  items.value.push({
    id: items.value.length +1, 
    label: newItem.value,
    highPriority: newItemHighPriority.value  
  });
  // Clean the input
  newItem.value = '';
  newItemHighPriority.value = false;
};

const doEdit = (edit) => {
  editing.value = edit;
  // Limpiando la entrada de texto
  // en caso de que se oculte o muestre
  // el formulario
  newItem.value = "";
  newItemHighPriority.value = false;
};

// --- Formulario ---
const newItem = ref("");
const newItemHighPriority = ref(false);
const iceCreamFlavors = ref([]);
const editing = ref(true);
const activateEdition = (activate) => {
  editing.value = activate;
};

// Alternando el esta de compra del item
const togglePurchased = (item) => {
  item.purchased = !item.purchased;
};

// Propiedad computada
const characterCount = computed(()=>{
  // Toda propiedad computada debe regresar un valor
  return newItem.value.length;
});

// Creando propiedad computada que invierte items de la lista
const reversedItems = computed(() => {
  return [...items.value].reverse();
});
//Alternativa para la creacion de la propiedad
// const reversedItems = computed(() => [...items.value].reverse());
</script>

<template>
  <div class="header">
    <h1>
   <i class="material-icons shopping-cart-icon">
    local_mall
  </i> 
    {{ header }} 
  </h1>

  <button 
  v-if="editing" 
  class="btn" 
  @click="activateEdition(false)">
  Cancelar
</button>

  <button 
  v-else class="btn btn-primary" 
  @click="activateEdition(true)">
  Agregar Articulo
</button>
  </div>

  <!--Agrupando entradas de usuario-->
  <form 
  v-on:submit.prevent="saveItem" 
  v-if="editing"
  class="add-item form">
  <input v-model="newItem" type="text" placeholder="Agregar un articulo" />

  <!--Caja de seleccion de Prioridad-->
  <label>
    <input type="checkbox" v-model="newItemHighPriority" />
    Alta Prioridad
  </label>
  
  <!--Boton-->
  <button 
  :disabled="newItem.length === 0" 
  class="btn btn-primary">
    Salvar Articulo
  </button>

  <!-- Contador -->
  <p class="counter">
    {{ characterCount }} / 200
  </p>
  </form>
  <ul></ul>
  {{ newItemHighPriority }}

  <!-- Lista clase con objetos-->
  <ul>
    <li 
    v-for="({label, id, purchased, priority}, index) in reversedItems" 
    @click="togglePurchased(reversedItems[index])"
    v-bind:key="id"
    :class="{strikeout: purchased, priority: priority}"> 
    {{ priority ? "⚡": "🛍️" }} {{  label }} 
    </li>
  </ul>
  <!--Lista con referencia al objeto-->
<!--
  <ul>
    <li
      v-for="item in items"
      @click="togglePurchased(item)"
      v-bind:key="item.id"
      :class="{ strikeout: item.purchased, item.priority: item.highPriority }">
      {{ priority ? "⚡": "🛍️" }} {{  label }}
    </li>
  </ul>
  -->
  <p v-if="items.length === 0">🥀 NO HAY ELEMENTOS EN LA LISTA 🥀</p>
</template>

<style scoped>
.shopping-cart-icon{
  font-size: 2rem;
}
</style>