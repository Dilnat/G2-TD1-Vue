<script setup lang="ts">
import ListeDeTaches from '@/composants/ListeDeTaches.vue';
import type { Ref } from 'vue';
import {ref} from "vue";
let id = 0;
interface TacheList {
  ids: number;
  titres:string;
}
const todoListes:Ref<TacheList[]> = ref([{ids:id, titres:"Tâches de Mattéo"},
  {ids:id++, titres: "Tâches de Tony"}]);
let nouvelleTacheList = ref("");
function ajouterTacheList(){
  if(nouvelleTacheList.value!=""){
    todoListes.value.push({ids:id++, titres:nouvelleTacheList.value});
    nouvelleTacheList.value = "";
  }
}
</script>

<template>
  <ul>
    <h2>Liste des Tâches</h2>
    <input type="texte" v-model.trim="nouvelleTacheList" placeholder="Ajouter une tâche">
    <button @click="ajouterTacheList">Valider</button>
    <li v-for="tacheList in todoListes" :key="tacheList.ids">
<!--      <input type="checkbox">-->
      <span>{{tacheList.titres}}</span>
      <button >Retirer</button>
    </li>
  </ul>



  <ListeDeTaches titre="tâches de Mattéo"/>
  <ListeDeTaches titre="tâches de Tony"/>
  <ListeDeTaches titre="tâches de Boris"/>
</template>

<style scoped>
</style>

