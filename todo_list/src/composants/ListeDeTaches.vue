<script setup lang="ts">
import {ref, computed} from 'vue';
import type { Ref } from 'vue';
import TacheElement from '@/composants/TacheElement.vue';
let id = 0;
const taches:Ref<Tache[]> = ref([{id:id++, description:"Apprendre Vue", faite:false},
  {id:id++, description:"Finir la SAÉ", faite:false},
  {id:id++, description:"Réviser pour l'interro", faite:false}]);
let nouvelleTache = ref("");
function ajouterTache(){
  if(nouvelleTache.value!=""){
    taches.value.push({id:id++, description:nouvelleTache.value, faite:false});
    nouvelleTache.value = "";
  }
}
function retirerTache(tache:Tache){
  taches.value = taches.value.filter(t => t.id !== tache.id);
}
interface Tache {
  id: number;
  description:string;
  faite:boolean;
}
const cacheFaits = ref(false);
const tachesFiltrees = computed(() => {return taches.value.filter(t => cacheFaits.value == false && t.faite == false);});

const props = defineProps<{titre: string}>();


</script>

<template>
  <div id="wrapper">
    <ul>
      <h2>{{titre}}<button @click="$emit('supprimerListe')">Retirer</button></h2>

      <input type="texte" v-model.trim="nouvelleTache" placeholder="Ajouter une tâche">
      <button @click="ajouterTache">Valider</button>
      <button @click="cacheFaits = !cacheFaits">
        {{ cacheFaits ? 'Tout montrer' : 'Cacher les tâches terminées' }}
      </button>
      <li v-for="tache in tachesFiltrees" :key="tache.id">
        <TacheElement :description-tache="tache.description" :cochee="tache.faite" />
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
.fait{
  text-decoration: line-through;
}
</style>