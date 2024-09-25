<script setup>
import{ref} from 'vue';
const header=ref('App lista de compras');
const items =ref([
    {id:'0', label:'10 Bolillos'},
    {id:'1', label:'1k Arroz'},
    {id:'2', label:'1k Azucar'},
    {id:'3', label:'1k Frijol'}
]);
const newitem = ref('')
const newitemspriority= ref('low')
</script>

<template>
<h1>{{header}}</h1>
<input v-mode="newitem" type="text" placeholder="Agregar Articulo">

<label><input type="radio" value="low" v-mode="newitemspriority">Bajo</label>
<label><input type="radio" value="high" v-mode="newitemspriority">Alto</label>
{{ newitemspriority =='low'?'hilo': 'fuegito'}}

<i class="material-icons shopping-cart-icon">local_mall</i>
<ul>
    <li v-for="item in items" v-bind:key="item.id">{{item.label}}</li>
</ul>
</template>

<style scoped>
.shopping-cart-icon{
font-size: 2rem;
}
</style>
