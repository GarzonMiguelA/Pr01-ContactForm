<script setup>
import { ref } from 'vue';
//Definimos los props y el emit para comunicar con el padre
const emit = defineEmits(['afegirContacte'])

const nom = ref('')
const telefon = ref('')


// Función para enviar los datos al componente padre
const submitContacte = () => {
  if (nom.value && telefon.value) {
    console.log('Nuevo contacto:', { nom: nom.value, telefon: telefon.value });
    emit('afegirContacte', { nom: nom.value, telefon: telefon.value });
    nom.value = '';
    telefon.value = '';
  }
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