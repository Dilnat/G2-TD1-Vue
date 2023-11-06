<script setup lang="ts">
let texte =  "un texte qui s'affiche";
let compteur = 7;
function incremente(){
  compteur++;
  console.log(compteur);
}
</script>


<template>
  <div id="wrapper">
    <h1>TODO liste</h1>
    <p>{{texte}}</p>
    <a v-bind:href="texte">Test</a>
    <button v-on:click="incremente">+</button>
  </div>
</template>

<style scoped>
</style>