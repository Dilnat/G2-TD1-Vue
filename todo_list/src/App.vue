<script setup lang="ts">
import ListeDeTaches from '@/composants/ListeDeTaches.vue';
import type { Ref } from 'vue';
import {ref} from "vue";
let id = 0;
interface TacheList {
  ids: number;
  titres:string;
}
const todoListes:Ref<TacheList[]> = ref([{ids:id++, titres:"Tâches de Mattéo"},
  {ids:id++, titres: "Tâches de Tony"}]);
let nouvelleTacheList = ref("");
function ajouterTacheList(){
  if(nouvelleTacheList.value!=""){
    todoListes.value.push({ids:id++, titres:nouvelleTacheList.value});
    nouvelleTacheList.value = "";
  }
}

function retirerListe(tacheList:TacheList){
  console.log(todoListes.value);
  console.log(tacheList);
  todoListes.value = todoListes.value.filter(t => t.ids !== tacheList.ids);
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
    </li>
  </ul>

  <ListeDeTaches  v-for="liste in todoListes" :key="liste.ids"  :titre="liste.titres" @supprimerListe="retirerListe(liste)" />
</template>

<style scoped>
</style>

