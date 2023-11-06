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
function retirerTache(tache){
  taches.value = taches.value.filter(t => t.id !== tache.id);
}
</script>

<template>
  <div id="wrapper">
    <ul>
      <input type="texte" v-model.trim="nouvelleTache" placeholder="Ajouter une tâche">
      <button @click="ajouterTache">Valider</button>
      <li v-for="tache in taches" :key="tache.id">
        <input type="checkbox" v-model="tache.faite">
        <span>{{tache.description}}</span>
        <button @click="retirerTache(tache)">Retirer</button>
      </li>
    </ul>
  </div>
</template>

<style scoped>
#wrapper{
  border-radius: 5px;
  border:solid black 2px;
  padding: 10px;
}
ul,span{
  padding:10px;
}
li{
  list-style: none;
  padding: 2px 0px;
}
</style>