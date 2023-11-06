<script setup lang="ts">
import {ref} from 'vue';
let id = 0;
const taches = ref([{id:id++, description:"Apprendre Vue", faite:false},
  {id:id++, description:"Finir la SAÉ", faite:false},
  {id:id++, description:"Réviser pour l'interro", faite:false}]);
let nouvelleTache = ref("");
function ajouterTache(){
  if(nouvelleTache.value!=""){
    taches.value.push({id:id++, description:nouvelleTache.value, faite:false});
    nouvelleTache.value = "";
  }
}
</script>

<template>
  <div id="wrapper">
    <ul>
      <input type="texte" v-model.trim="nouvelleTache" placeholder="Ajouter une tâche">
      <button @click="ajouterTache">Valider</button>
      <li v-for="tache in taches" :key="tache.id">
        <span>{{tache.description}}</span>
      </li>
    </ul>
  </div>
</template>

<style scoped>
</style>