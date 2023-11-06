<script setup lang="ts">
import {ref} from 'vue';
let id = 0;
const taches = ref([{id:id++, description:"Apprendre Vue", faite:false},
  {id:id++, description:"Finir la SAÉ", faite:false},
  {id:id++, description:"Réviser pour l'interro", faite:false}]);
</script>

<template>
  <div id="wrapper">
    <ul>
      <li v-for="tache in taches" :key="tache.id">
        <span>{{tache.description}}</span>
      </li>
    </ul>
  </div>
</template>

<style scoped>
</style>