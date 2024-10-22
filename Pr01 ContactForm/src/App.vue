<script setup>
// Importamos funciones ref y computed de Vue:
import { ref, computed } from 'vue';
// Importamos componente hijo contacto:
import contacto from './components/contacto.vue';

//Creamos las var para guardar:
const contactes = ref([]);
const searchQuery = ref(''); 

// Gestionamos el envío del formulario y añadimos contacto:
const afegirContacte = (nouContacte) => {
  contactes.value.push(nouContacte); //Añadimos el contacto al array 
};

// Filtrar con computed los contactos por nombre:
const filteredContactes = computed(() => {
  return contactes.value.filter(contacte => 
    contacte.nom.toLowerCase().includes(searchQuery.value.toLowerCase()) // Filtramos contactos
  );
});
</script>

<template>
  <!-- Incluimos el componente hijo: -->
  <contacto @afegirContacte="afegirContacte" />

  <!-- Input para buscar por nombre: -->
  <div>
    <label for="search">Buscar por nombre:</label>
    <input id="search" type="text" v-model="searchQuery" placeholder="Buscar contactos..." />
  </div>

  <!-- Mostramos la lista de contactos filtrados: -->
  <h2>Contactos añadidos:</h2>
  <ul>
    <!-- Con for mostramos la lista, poco a poco: -->
    <li v-for="(contacte, index) in filteredContactes" :key="index">
      {{ contacte.nom }}
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
