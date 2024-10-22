<script setup>
import { ref } from 'vue';
import contacto from './components/contacto.vue';

//Creamos las variable para almacenar el nombre y numero:
const contactes = ref([])

// Funció per gestionar l'enviament del formulari
const afegirContacte = (nouContacte) => {
  contactes.value.push(nouContacte)
}
</script>

<template>
  <!-- Incluimos el componente hijo -->
  <contacto @afegirContacte="afegirContacte" />

  <!-- Mostrar la lista de contactos -->
  <h2>Contactos añadidos:</h2>
  <ul>
    <li v-for="(contacte, index) in contactes" :key="index">
      {{ contacte.nom }} - 
      <a :href="'tel:' + contacte.telefon">{{ contacte.telefon }}</a>
    </li>
  </ul>

</template>



<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
