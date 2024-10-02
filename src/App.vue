<script setup>
import { ref } from "vue";
const header = ref('lista de Compras');
//----items---
//item-model
const items = ref([
    {id:'0', label: '1 kG de carne✨'}, 
    {id:'1', label: '1 bolsa de proteina 🦾 '}, 
    {id:'2', label: '1 Caja de Huevos 🥚'},
    {id:'3', label: '1kG de creatina 💪'}
]);
//items
const saveitems=() => {
  items.value.push({id: items.value.length + 1, label: newItem.value}); 
  //limpia 
  newItem.value=""; 
};
// --- visualizacion formulario -----
const newItem = ref(''); 
const newItemHighPriority = ref(false);
const editing=ref(true);
const activateedit=(avtivate) =>{
    editing.value=activate;
}


</script>

<template>
    <div class="header">
        <h1>
    <i class="material-icons shopping-cart-icon">local_mall</i>
    {{ header }}
</h1>
<button  v-if="editing" class="btn" @click="activateedit(false)">❌Cancelar</button>
<button  v-else class="btn btn-primary" @click="activateedit(true)"> ⬆ Agregar Articulo</button>
    </div>

<form 
class="add-item fomr"
v-if="editing"
 v-on:submit.prevent="saveitems()">
    <input type="text" 
    placeholder="Agregar"  
    v-model.trim="newItem">
    <label>
      <input type="checkbox" v-model="newItemHighPriority" />
      Alta prioridad
    </label>
 <br>
 <br>
    <button class="btn btn-primary">
    Guardar</button>
  
</form>
    
    <ul>
        <li v-for="({id,label}, i) in items" :key="id"> {{ i+1 }} {{i%2==0?'🌺':'🌹'}} {{label}} </li>
    </ul>

    <p  v-if="items.length === 0">🥀 NO HAY ELEMENTOS EN LA LISTA 🥀</p>
</template>

<style scoped>
.shopping-cart-icon{
    font-size: 2rem;
}
</style>