<script setup>
import { ref } from 'vue';
// Modelo
const header = ref('App lista de compras');
//---Items---
//Item-model
const items = ref([
  {id:'0', label: 'Shampoo'},
  {id:'1', label: 'Papel de baño'},
  {id:'2', label: 'Jabon'},
  {id:'3', label: 'Mayonesa'}
]);
//Item-method
const saveItem=()=>{
   items.value.push({id:items.value.length + 1, label: newItem.value});
   //Limpia el input
   newItem.value='';
};


const newItem = ref("");
const newItemHighPriority = ref(false);
const editing=ref(true);
const activateEdition=(activate)=>{
  editing.value =activate;
}
</script>

<template>
  <h1>
   <i class="material-icons shopping-cart-icon">local_mall</i> 
    {{ header }} 
  </h1>
  <button v-if="editing"class="btn" @click="activateEdition(false)">Cancelar</button>
  <button v-else class="btn btn-primary" @click="activateEdition(true)">Agregar articulo</button>
  <form class="add-item form"
  v-if="editing"
  v-on:submit.prevent></form>
  <form v-on:submit.prevent="saveItem()">
  <input v-model="newItem" type="text" placeholder="Agregar un articulo" />
  <!--Caja de seleccion de Prioridad-->
  <label>
    <input type="checkbox" v-model="newItemHighPriority" />
    Alta Prioridad
  </label>
  <!--Boton-->
  <button class="btn btn-primary">
    Salvar Articulo
  </button>
  </form>
  <ul></ul>

  {{ iceCreamFlavors }}
  <ul></ul>
  {{ newItemHighPriority }}
  <!-- Lista -->
  <ul>
    <li v-for="item in items" :key="item.id"> ✔️ {{  item.label }} </li>
  </ul>
  <p v-if="items.length ===0">🥀 NO HAY ELEMENTOS EN LA LISTA 🥀</p>
</template>

<style scoped>
.shopping-cart-icon{
  font-size: 2rem;
}
</style>