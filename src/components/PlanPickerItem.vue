<template>
    <div @click="selectPlan" class="plan">
      <div class="description">
        <span class="title">{{ name }} {{ selected ? '🎃': '' }}</span>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  // Usando un macro para
  // definir las props
  const props = defineProps({
    name:{
    type: String,
    required: true
  },
  
  });
  //Define event
  const emit=defineEmits(['select']);
  //Variable que permite recordar si el plan no ha sido seleccionado
  const selected= ref(false);
  //Funcion que permite cambiar el valor de la variable
  const selectPlan= () =>{
  selected.value =[selected.value];
  emit('select',props)
   //Emitir evento de que el plan ha sido seleccionado

  };

  </script>
  
  <style scoped>
  
  </style>