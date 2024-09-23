<script setup>
import{ref} from 'vue';
const header=ref('App lista de compras');
const items =ref([
    {id:'0', label:'10 Bolillos'},
    {id:'1', label:'1k Arroz'},
    {id:'2', label:'1k Azucar'},
    {id:'3', label:'1k Frijol'}
]);
</script>

<template>
<h1>{{header}}</h1>
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
