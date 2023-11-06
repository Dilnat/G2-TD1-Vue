<script setup lang="ts">
import {ref} from 'vue';
let texte =  "un texte qui s'affiche";
let compteur = ref(7);
function incremente(){
  compteur.value++;
  console.log(compteur.value);
}
// function onInput(e) {
//   compteur.value = e.target.value
// }
</script>


<template>
  <div id="wrapper">
    <h1>TODO liste</h1>
    <p>{{texte}}</p>
    <a v-bind:href="texte">Test</a>
    <button v-on:click="incremente">+</button>
<!--    <input v-bind:value="compteur" v-on:input="compteur">-->
    <input v-model="compteur">
  </div>
</template>

<style scoped>
</style>