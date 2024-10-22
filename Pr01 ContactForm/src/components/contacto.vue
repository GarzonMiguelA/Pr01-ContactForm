<script setup>
import { ref } from 'vue';// Importamos la función 'ref' de Vue para crear variables reactivas

//Definimos props y el emits para comunicar con el padre
const emit = defineEmits(['afegirContacte']) // Emitimos evento 'afegirContacte' que el padre puede escuchar

//Creamos las variables para guardar nombre y telf.:
const nom = ref('')
const telefon = ref('')

// Creamos función para enviar datos al padre
const submitContacte = () => {
  console.log('Nuevo contacto:', { nom: nom.value, telefon: telefon.value });
  emit('afegirContacte', { nom: nom.value, telefon: telefon.value });
  nom.value = ''; // Dejamos vacio el campo
  telefon.value = ''; // Dejamos vacio el campo
}
</script>

<template>
  <form @submit.prevent="submitContacte" >
    <div>
        <label for="nom">Nombre:</label>
        <input id='nom' type="text" v-model="nom"> 
    </div>
    <div>
      <label for="telefon">Número de teléfono:</label>
      <input id="telefon" type="tel" v-model="telefon" />
    </div>
    <button type="submit">Añadir contacto</button>
  </form>
</template>